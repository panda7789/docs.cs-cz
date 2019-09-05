---
title: Řetězcové kanonické funkce
ms.date: 03/30/2017
ms.assetid: 5e2cbebd-5df3-47c7-b0e2-49a17ab22bfb
ms.openlocfilehash: 9013b8bd8505442666dd0688eaf2586959a61b70
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249095"
---
# <a name="string-canonical-functions"></a>Řetězcové kanonické funkce
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]zahrnuje řetězcové kanonické funkce.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny řetězcové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|`Concat(string1, string2)`|Vrátí řetězec, který obsahuje `string2` připojení k. `string1`<br /><br /> **Argumenty**<br /><br /> `string1`: Řetězec, ke kterému `string2` se připojí.<br /><br /> `string2`: Řetězec, který je připojen k `string1`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`. Pokud je délka řetězce návratové hodnoty větší než maximální povolená délka, dojde k chybě.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Contains(string, target)`|Vrátí `true` , `target` Pokud je obsažen `string`v.<br /><br /> **Argumenty**<br /><br /> `string`: Hledaný řetězec.<br /><br /> `target`: Cílový řetězec, který je prohledáván.<br /><br /> **Návratová hodnota**<br /><br /> `true`Pokud `target` je obsažen v `string`, jinak `false`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `Contains('abc', 'bc')`|  
|`EndsWith(string, target)`|Vrátí `true` ,`string`Pokud `target` končí na.<br /><br /> **Argumenty**<br /><br /> `string`: Hledaný řetězec.<br /><br /> `target`: Cílový řetězec hledaný na konci `string`.<br /><br /> **Návratová hodnota**<br /><br /> `True`Pokud `string` `false`končí na, v opačném případě. `target`<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `EndsWith('abc', 'bc')`**Poznámka:**  Pokud používáte poskytovatele dat SQL Server, tato funkce vrátí `false` , zda je řetězec uložen ve sloupci řetězce s pevnou délkou a `target` je konstanta. V tomto případě je prohledán celý řetězec, včetně všech koncových mezer. Možným řešením je zkrátit data v řetězci s pevnou délkou, jako v následujícím příkladu:`EndsWith(TRIM(string), target)`|  
|`IndexOf(target, string)`|Vrátí pozici `target` uvnitř `string`nebo 0, pokud nebyla nalezena. Vrátí hodnotu 1, aby označovala `string`začátek. Číslování indexu začíná 1.<br /><br /> **Argumenty**<br /><br /> `target`: Řetězec, který se má vyhledat.<br /><br /> `string`: Hledaný řetězec.<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 4.`<br /><br /> `IndexOf('xyz', 'abcxyz')`|  
|`Left(string, length)`|Vrátí první `length` znaky z levé `string`strany. Pokud `string` je délka menší než `length`, vrátí se celý řetězec.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: A `Int16` ,`Int32`, nebo`Byte`. `Int64` `length`nemůže být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `Left('abcxyz', 3)`|  
|`Length(string)`|Vrátí délku (`Int32`) řetězce v počtu znaků.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `Int32`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns 6.`<br /><br /> `Legth('abcxyz')`|  
|`LTrim(string)`|Vrátí `string` bez úvodní prázdné znaky.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `LTrim('   abc')`|  
|`Replace(string1, string2, string3)`|Vrátí `string1`všechny výskyty `string2` nahrazené `string3`.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abcxyz.`<br /><br /> `Concat('abc', 'xyz')`|  
|`Reverse(string)`|Vrátí `string` hodnotu s obráceným pořadím znaků.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns dcba.`<br /><br /> `Reverse('abcd')`|  
|`Right(string, length)`|Vrátí poslední `length` znaky `string`z. Pokud `string` je délka menší než `length`, vrátí se celý řetězec.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `length`: A `Int16` ,`Int32`, nebo`Byte`. `Int64` `length`nemůže být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Right('abcxyz', 3)`|  
|`RTrim(string)`|Vrátí `string` bez koncového prázdného místa.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.|  
|`Substring(string, start, length)`|Vrátí podřetězec řetězce, který začíná na pozici `start`, s `length` délkou znaků. Začátek 1 označuje první znak řetězce. Číslování indexu začíná 1.<br /><br /> **Argumenty**<br /><br /> `string`: A `String`.<br /><br /> `start`: A`Int64` , a`Int32` .`Byte` `Int16` `start`nemůže být menší než jedna.<br /><br /> `length`: A`Int64` , a`Int32` .`Byte` `Int16` `length`nemůže být menší než nula.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns xyz.`<br /><br /> `Substring('abcxyz', 4, 3)`|  
|`StartsWith(string, target)`|Vrátí `true` ,`target`Pokud `string` začíná na.<br /><br /> **Argumenty**<br /><br /> `string`: Hledaný řetězec.<br /><br /> `target`: Cílový řetězec hledaný na začátku `string`.<br /><br /> **Návratová hodnota**<br /><br /> `True`Pokud `string` `false`začíná na, v opačném případě. `target`<br /><br /> **Příklad**<br /><br /> `-- The following example returns true.`<br /><br /> `StartsWith('abc', 'ab')`|  
|`ToLower(string)`|Vrátí `string` s velkými písmeny převedenými na malá písmena.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `ToLower('ABC')`|  
|`ToUpper(string)`|Vrátí `string` s malými písmeny převedenými na velká písmena.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns ABC.`<br /><br /> `ToUpper('abc')`|  
|`Trim(string)`|Vrátí `string` bez úvodní a koncové mezery.<br /><br /> **Argumenty**<br /><br /> A `String`.<br /><br /> **Návratová hodnota**<br /><br /> A `String`.<br /><br /> **Příklad**<br /><br /> `-- The following example returns abc.`<br /><br /> `Trim('      abc   ')`|  
  
 Tyto funkce budou v `null` případě zadaného `null` vstupu vráceny.  
  
 Ekvivalentní funkce jsou k dispozici ve spravovaném zprostředkovateli klienta Microsoft SQL. Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Viz také:

- [Kanonické funkce](canonical-functions.md)
