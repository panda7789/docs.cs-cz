---
title: Informace o volajícím
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 93fb1e327d65ac19f293a2f77b7d5712fc5e8d2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400665"
---
# <a name="caller-information-visual-basic"></a>Informace o volajícím (Visual Basic)
Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.  
  
 Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou definovány v <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů:  
  
|Atribut|Description|Typ|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti volajícího. Viz [názvy členů](#MEMBERNAMES) dále v tomto tématu.|`String`|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití atributů Informace o volajícím. Při každém volání `TraceMessage` metody jsou informace o volajícím nahrazeny jako argumenty nepovinných parametrů.  
  
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
  
 Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledků <xref:System.Exception.StackTrace%2A> vlastnosti pro výjimky nejsou výsledky ovlivněny zmatením.  
  
 Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a>Názvy členů  
 Atribut lze použít `CallerMemberName` k zamezení zadání názvu člena jako `String` argumentu volané metody. Pomocí této techniky se vyhnete problému s tím, že **Refaktoring přejmenování** hodnoty nemění `String` . Tato výhoda se hodí zvláště v těchto úlohách:  
  
- Použití trasování a diagnostických rutin.  
  
- Implementace <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní při vázání dat. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez `CallerMemberName` atributu je nutné zadat název vlastnosti jako literál.  
  
 Následující graf znázorňuje názvy členů, které jsou vráceny při použití `CallerMemberName` atributu.  
  
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

- [Atributy (Visual Basic)](../../language-reference/attributes.md)
- [Společné atributy (Visual Basic)](attributes/common-attributes.md)
- [Volitelné parametry](../language-features/procedures/optional-parameters.md)
- [Koncepty programování (Visual Basic)](index.md)
