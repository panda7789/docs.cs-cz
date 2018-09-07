---
title: Informace o volajícím (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 048e91ad337f74ef04a2a03412a44a0be0ef9506
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047893"
---
# <a name="caller-information-c"></a>Informace o volajícím (C#)
Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.  
  
 Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti volajícího. Zobrazit [názvy členů](#MEMBERNAMES) dále v tomto tématu.|`String`|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití atributů Informace o volajícím. Pro všechna volání `TraceMessage` metoda, informace o subjektu volajícím nahrazeny v podobě argumentů pro volitelné parametry.  
  
```csharp  
public void DoProcessing()  
{  
    TraceMessage("Something happened.");  
}  
  
public void TraceMessage(string message,  
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",  
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",  
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)  
{  
    System.Diagnostics.Trace.WriteLine("message: " + message);  
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);  
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);  
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);  
}  
  
// Sample Output:  
//  message: Something happened.  
//  member name: DoProcessing  
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a>Poznámky  
 Pro každý volitelný parametr je třeba zadat explicitní výchozí hodnotu. Atributy Informace o volajícím nelze použít u parametrů, které nejsou uvedeny jako volitelné.  
  
 Atributy Informace o volajícím neučiní parametr volitelným. Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán.  
  
 Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledků <xref:System.Exception.StackTrace%2A> pro výjimky, výsledky nejsou ovlivněny obfuskací.  
  
 Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.  
  
###  <a name="MEMBERNAMES"></a> Názvy členů  
 Můžete použít `CallerMemberName` atribut vyhnout zadávání názvu členu jako `String` argumentů volané metody. Tímto způsobem se vyhnete problému, který **refaktoring přejmenování** nedojde ke změně `String` hodnoty. Tato výhoda se hodí zvláště v těchto úlohách:  
  
-   Použití trasování a diagnostických rutin.  
  
-   Implementace <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní při vytvoření vazby mezi daty. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez `CallerMemberName` atribut, musíte zadat název vlastnosti jako literál.  
  
 Následující graf ukazuje názvy, které jsou vráceny při použití členů `CallerMemberName` atribut.  
  
|K volání dochází v rámci|Výsledek názvu členu|  
|-------------------------|------------------------|  
|Metoda, vlastnost nebo událost|Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.|  
|Konstruktor|Řetězec „.ctor“|  
|Statický konstruktor|Řetězec „.cctor“|  
|Destruktor|Řetězec „Finalize“|  
|Operátory nebo převody definované uživatelem|Vygenerovaný název pro člen, například „op_Addition“.|  
|Konstruktor atributu|Název členu, na který se atribut používá. Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.|  
|Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)|Výchozí hodnota volitelného parametru.|  
  
## <a name="see-also"></a>Viz také

- [Atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Běžné atributy (C#)](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
- [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [Koncepty programování (C#)](../../../csharp/programming-guide/concepts/index.md)
