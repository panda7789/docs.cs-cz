---
title: Informace o subjektu volajícím (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 0074ad5bfa5907fb1d02cc92b8b5717897a36b3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644209"
---
# <a name="caller-information-visual-basic"></a>Informace o subjektu volajícím (Visual Basic)
Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.  
  
 Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> obor názvů:  
  
|Atribut|Popis|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti volajícího. V tématu [názvy členů](#MEMBERNAMES) dál v tomto tématu.|`String`|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití atributů Informace o volajícím. Při každém volání `TraceMessage` metoda, informace o subjektu volajícím je nahrazena jako argumenty pro volitelné parametry.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
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
 [Atributy (Visual Basic)](../../../visual-basic/language-reference/attributes.md)  
 [Mezi běžné atributy (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
 [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Programování konceptů (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
