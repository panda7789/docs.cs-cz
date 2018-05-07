---
title: Informace o subjektu volajícím (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 6f0cd4d9d8fc85cb15431ccb4c76eee14b3f67c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="caller-information-c"></a>Informace o subjektu volajícím (C#)
Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.  
  
 Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti volajícího. V tématu [názvy členů](#MEMBERNAMES) dál v tomto tématu.|`String`|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití atributů Informace o volajícím. Při každém volání `TraceMessage` metoda, informace o subjektu volajícím je nahrazena jako argumenty pro volitelné parametry.  
  
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
  
 Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledky <xref:System.Exception.StackTrace%2A> maskováním nemá vliv vlastnost pro výjimky, výsledky.  
  
 Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.  
  
###  <a name="MEMBERNAMES"></a> Názvy členů  
 Můžete použít `CallerMemberName` atribut Vyhněte se zadání název člena jako `String` argument volané metodě. Pomocí Tato technika tomuto problému vyhnout, **přejmenovat refaktoring** nezmění `String` hodnoty. Tato výhoda se hodí zvláště v těchto úlohách:  
  
-   Použití trasování a diagnostických rutin.  
  
-   Implementace <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní při vytváření vazby data. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez `CallerMemberName` atribut, musíte zadat název vlastnosti jako literál.  
  
 Následující tabulka ukazuje člen názvy, které jsou vráceny při použití `CallerMemberName` atribut.  
  
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
 [Atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Mezi běžné atributy (C#)](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
 [Pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [Programování konceptů (C#)](../../../csharp/programming-guide/concepts/index.md)
