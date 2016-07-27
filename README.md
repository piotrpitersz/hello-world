1.
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

2.------------------------------------------------------------------------------------------------------------

function bold() {
                var txta = document.getElementById('txt');
                if (txta.selectionStart || txta.selectionStart == "0") {
                    var strt = txta.selectionStart;
                    var end = txta.selectionEnd;
                    var tag_txt = '<del>' + txta.value.substring(strt, end) + '</del>';
                    txta.value = txta.value.substring(0, strt) + tag_txt + txta.value.substring(end, txta.value.length);
                    
                    txta.selectionRange((end + '<del>'.length), (end + '<del>'.length));
                    txta.focus();
                }
                return tag_txt;
            }


2b.------------------------------------------------

function bold() {
                var textArea = document.getElementById('txt');
                var start = textArea.selectionStart;
                var end = textArea.selectionEnd;
                var replacement = '<del>' + textArea.value.substring(start, end) + '</del>';
                textArea.value = textArea.value.substring(0, start) + replacement + textArea.value.substring(end, textArea.value.length);
                return replacement;
            }

2c.-------------------------------------------------

function bold() {
                var el = document.getElementById('txt');
                el.value = el.value.substring(0, el.selectionStart) + '<del>' + 
                el.value.substring(el.selectionStart, el.selectionEnd) + '</del>' + el.value.substring(el.selectionEnd);
}

2d.--------------------------------------------------

            function bold() {
                var el = document.getElementById('txt');
                el.value = el.value.slice(0, el.selectionStart) + '<del>' +  
                el.value.slice(el.selectionStart, el.selectionEnd) + '</del>' + el.value.slice(el.selectionEnd);
