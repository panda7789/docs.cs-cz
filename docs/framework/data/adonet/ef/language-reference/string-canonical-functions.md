---
title: Kanonické funkce řetězce
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: 98274374275e4f07a7e5411e29504608c76c0fdc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="string-canonical-functions"></a>Kanonické funkce řetězce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje kanonické funkce řetězec.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`Concat (` `string1`, `string2``)`|Vrátí řetězec, který obsahuje `string2` připojenou k `string1`.<br /><br /> **Argumenty**<br /><br /> `string1`: Řetězec, který `string2` se připojí.<br /><br /> `string2`: Řetězec, který se připojí k `string1`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`. Pokud je délka řetězce návratovou hodnotu větší než maximální povolenou délku, dojde k chybě.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains (` `string`, `target``)`|Vrátí `true` Pokud `target` je součástí `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> `target`: Cílový řetězec, který je hledán.<br /><br /> **Návratová hodnota**<br /><br /> `true` Pokud `target` je součástí `string`jinak `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith (` `string`, `target``)`|Vrátí `true` Pokud `target` končí `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> `target`: Cílový řetězec vyhledávat na konci `string`.<br /><br /> **Návratová hodnota**<br /><br /> `True` Pokud `string` končí `target`jinak `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **Poznámka:** Pokud jsou pomocí poskytovatele dat systému SQL Server, funkce vrátí hodnotu `false` Pokud řetězec uložený ve sloupci řetězec pevnou délkou a `target` konstanta. V takovém případě je prohledána celý řetězec, včetně všech odsazení koncové mezery. Možným řešením je oříznout data v řetězce pevné délky, jako v následujícím příkladu: `EndsWith(TRIM(string), target)`|  
|`IndexOf(` `target`, `string``)`|Vrátí pozici `target` uvnitř `string`, nebo 0, pokud není nalezena. Vrátí hodnotu 1 označující začátek `string`. Index číslování spustí od 1.<br /><br /> **Argumenty**<br /><br /> `target`: Řetězec, který je hledán.<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left (` `string`, `length``)`|Vrátí první `length` znaků od levé straně `string`. Pokud délka `string` je menší než `length`, bude vrácen celý řetězec.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, `Int32`, `Int64`, Nebo `Byte`. `length` nesmí být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length (` `string` `)`|Vrátí (`Int32`) délka ve znacích řetězce.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(` `string` `)`|Vrátí `string` bez úvodní mezery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace (` `string1`, `string2`, `string3``)`|Vrátí `string1`, se všechny výskyty `string2` nahrazuje `string3`.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse (` `string` `)`|Vrátí `string` s pořadím znaky vrátit zpět.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right (` `string`, `length``)`|Vrátí poslední `length` znaků z `string`. Pokud délka `string` je menší než `length`, bude vrácen celý řetězec.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: `Int16`, `Int32`, `Int64`, Nebo `Byte`. `length` nesmí být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(` `string` `)`|Vrátí `string` bez koncové mezery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.|  
|`Substring (` `string`, `start`, `length``)`|Vrátí dílčí řetězec řetězce začínající na pozici `start`, s délkou `length` znaků. Začátek 1 určuje první znak řetězce. Index číslování spustí od 1.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `start`: `Int16`, `Int32`, `Int64` a `Byte`. `start` nemůže být nižší než jednou.<br /><br /> `length`: `Int16`, `Int32`, `Int64` a `Byte`. `length` nesmí být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith (` `string`, `target``)`|Vrátí `true` Pokud `string` začíná `target`.<br /><br /> **Argumenty**<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> `target`: Cílový řetězec vyhledávat na začátku `string`.<br /><br /> **Návratová hodnota**<br /><br /> `True` Pokud `string` začíná `target`jinak `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(` `string` `)`|Vrátí `string` s převeden na malá písmena velká písmena.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(` `string` `)`|Vrátí `string` s malá písmena převeden na velká písmena.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(` `string` `)`|Vrátí `string` bez úvodní a koncové mezery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Vrátí tyto funkce `null` -li zadány `null` vstupní.  
  
 Ekvivalentní funkce je k dispozici ve zprostředkovateli spravované klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
