# getCoords

Функция позволяет преобразовать координаты из вида "градусы, минуты, секунды":

<pre> DD/1,MM/1,SS/100000, DD/1,MM/1,SS/100000</pre>

 В вид "десятичные доли градуса":
 
 <pre>DD.DDDDD, DD.DDDDD</pre>

Формула для пересчета:

<pre>DDD = DD + MM/60 + SS/3600</pre>

Вызов функции:

<pre>print_r(getCoords(array('49/1,57/1,438047/100000','82/1,36/1,2434283/100000')));</pre>

<pre>function getCoords($out){
	$coords = array("latitude","longitude");
	$date = array(1,60,3600);
	foreach($coords as $k => $v){
		$lats = '';
		$lat = explode(",", $out[$k]);
		for($i = 0; $i <= 2; $i++){
			$c = explode("/", $lat[$i]);
			$lats += $c[0] / $c[1] / $date[$i];
		}
		unset($coords[$k]);
		$coords[$v] = round($lats,6);
	}
	return $coords;
}</pre>
