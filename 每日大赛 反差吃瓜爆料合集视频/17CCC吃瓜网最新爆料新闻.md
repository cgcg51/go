### [👉👉点此进入♥观看入口👈👈](http://a.d44k.cc/hl.html)
<br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br><br></br># 用于平滑效果的缓冲区
        self lip_points_buffer = deque(maxlen=5)
    
    def get_lip_points(self, face_points):
        """提取嘴唇区域的68个关键点中的48-68点"""
        lip_points = []
        for i in range(48, 68):
            lip_points append((face_points part(i) x, face_points part(i) y))
        return np array(lip_points, np int32)
    
    def apply_lipstick(self, frame, lip_points):
        """应用口红效果"""
        # 创建嘴唇区域的掩码
        mask = np zeros(frame shape[:2], dtype=np uint8)
        cv2 fillPoly(mask, [lip_points], 255)
        
        # 获取当前选择的口红颜色
        current_color = self lipstick_colors[self current_color_index]
        
        # 应用颜色到嘴唇区域
        frame[mask == 255] = frame[mask == 255] * 0 5 + current_color * 0 5  # 混合效果
        
        # 绘制嘴唇轮廓
        cv2 polylines(frame, [lip_points], isClosed=True, color=(255, 255, 255), thickness=1)
