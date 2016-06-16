# gui
createtime 20160522

//基于ThinkPHP，计算一个页面的访问次数。
$last_view = session('last_view_service');
        $time = time();
        if ($last_view + 10 < $time) { //每10秒计算一次。10秒内访问算一次
            $data['uid'] = $this->uid;
            $data['type'] = 'service';
            $data['row_id'] = $aId;
            $data['to_uid'] = $service['uid'];
            D('WekoStat')->addVisit($data);
            session('last_view_service', $time, 20);
        }
