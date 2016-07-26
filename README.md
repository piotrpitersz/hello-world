<?php

    $t = 'banan';    
    
    $where = '';
    
    if (strpos($t, " ") !== false)
    {
        $words = str_getcsv($t, " ");
        
        foreach ($words as $w)
        {
            if (strpos($w, " ") !== false)
            {
                $where .= " AND x LIKE '%" . $w . "%' ";
            }
            else
            {                
                $where .= " AND x RLIKE '[[:<:]]" . $w . "[[:>:]]'";                
            }
        }        
    }
    else
    {
        $where .= " AND x LIKE '%" . $t . "%' ";
    }
    
    $q = 'SELECT * FROM table WHERE y="lala" ' . $where;
    
    echo $q;
    
?>

http://stackoverflow.com/questions/38574396/split-text-under-few-conditions-php
