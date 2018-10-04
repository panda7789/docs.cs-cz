---
title: Řetězcové kanonické funkce
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: d4758f8325b99bc4bd91575dd774d2dabde1f925
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580625"
---
# <a name="string-canonical-functions"></a>Řetězcové kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] zahrnuje řetězcové kanonické funkce.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Vrátí řetězec, který obsahuje `string2` připojenou k `string1`.<br /><br /> **Argumenty**<br /><br /> `string1`: Řetězec, který `string2` se připojí.<br /><br /> `string2`: Řetězec, který se připojí k `string1`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`. Pokud délka řetězce návratová hodnota je větší než maximální povolenou délku, dojde k chybě.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Vrátí `true` Pokud `target` je součástí `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> `target`: Cílový řetězec, který se hledá.<br /><br /> **Návratová hodnota**<br /><br /> `true` Pokud `target` je součástí `string`; jinak vrátí hodnotu `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Vrátí `true` Pokud `target` končí `string`.<br /><br /> **Argumenty**<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> `target`: Cílový řetězec prohledána na konci `string`.<br /><br /> **Návratová hodnota**<br /><br /> `True` Pokud `string` končí `target`; jinak vrátí hodnotu `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')` **Poznámka:** Pokud použijete poskytovatele dat SQL serveru, tato funkce vrací `false` Pokud je řetězec uložen ve sloupci řetězec pevné délky a `target` je konstanta. V takovém případě je prohledána celý řetězec, včetně všech odsazení koncové mezery. Oříznout data v řetězce pevné délky, jako v následujícím příkladu je možná alternativní řešení: `EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Vrátí pozici `target` uvnitř `string`, nebo 0, pokud není nalezena. Vrátí hodnotu 1 pro označení začátku `string`. Číslování indexu začíná od 1.<br /><br /> **Argumenty**<br /><br /> `target`: Řetězec, který se hledá.<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|Vrátí první `length` znaků z levé strany `string`. Pokud délka `string` je menší než `length`, vrátí se celý řetězec.<br /><br /> **Argumenty**<br /><br /> `string`: ODPOVĚĎ `String`.<br /><br /> `length`: Celé `Int16`, `Int32`, `Int64`, nebo `Byte`. `length` nemůže být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Vrátí (`Int32`) délka ve znacích, řetězce.<br /><br /> **Argumenty**<br /><br /> `string`: ODPOVĚĎ `String`.<br /><br /> **Návratová hodnota**<br /><br /> `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Vrátí `string` bez úvodních mezer.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Vrátí `string1`, se všechny výskyty `string2` nahrazuje `string3`.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Vrátí `string` s pořadí znaků vrátit zpět.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Vrátí poslední `length` znaky `string`. Pokud délka `string` je menší než `length`, vrátí se celý řetězec.<br /><br /> **Argumenty**<br /><br /> `string`: ODPOVĚĎ `String`.<br /><br /> `length`: Celé `Int16`, `Int32`, `Int64`, nebo `Byte`. `length` nemůže být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Vrátí `string` bez koncové prázdné znaky.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.|  
|`Substring(string, start, length)`|Vrátí dílčí řetězec z řetězce, počínaje na pozici `start`, s délkou `length` znaků. Začátek 1 označuje první znak řetězce. Číslování indexu začíná od 1.<br /><br /> **Argumenty**<br /><br /> `string`: ODPOVĚĎ `String`.<br /><br /> `start`: Celé `Int16`, `Int32`, `Int64` a `Byte`. `start` nemůže být nižší než jednou.<br /><br /> `length`: Celé `Int16`, `Int32`, `Int64` a `Byte`. `length` nemůže být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Vrátí `true` Pokud `string` začíná `target`.<br /><br /> **Argumenty**<br /><br /> `string`: Řetězec, který je vyhledán.<br /><br /> `target`: Hledali cílový řetězec na začátku `string`.<br /><br /> **Návratová hodnota**<br /><br /> `True` Pokud `string` začíná `target`; jinak vrátí hodnotu `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Vrátí `string` s převedený na malá písmena velká písmena.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Vrátí `string` s malá písmena převedena na velká písmena.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Vrátí `string` bez úvodní a koncové prázdné znaky.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.  
  
 Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL. Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
