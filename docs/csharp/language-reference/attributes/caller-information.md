---
title: 'C# Rezervované atributy: Sledování informací o volajícím'
ms.date: 04/09/2020
description: Tyto atributy pokyn kompilátor generovat informace o kódu, který volá člena. Pomocí CallerFilePath, CallerLineNumber a CallerMemberName můžete poskytnout podrobné informace o trasování
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389875"
---
# <a name="reserved-attributes-determine-caller-information"></a>Vyhrazené atributy: Určení informací o volajícím

Pomocí atributů info získáte informace o volajícím k metodě. Získáte cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a jméno člena volajícího. Chcete-li získat informace o volajícím člena, použijte atributy, které jsou použity pro volitelné parametry. Každý volitelný parametr určuje výchozí hodnotu. V následující tabulce jsou uvedeny atributy <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informace o volajícím, které jsou definovány v oboru názvů:

|Atribut|Popis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Úplná cesta je cesta v době kompilace.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ze kterého je metoda volána.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo název vlastnosti volajícího.|`String`|

Tyto informace vám pomohou psát trasování, ladění a vytváření diagnostických nástrojů. Následující příklad ukazuje, jak používat atributy informací o volajícím. Při každém volání `TraceMessage` metody informace o volajícím je nahrazen jako argumenty volitelné parametry.

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

Pro každý volitelný parametr zadáte explicitní výchozí hodnotu. Atributy informací o volajícím nelze použít na parametry, které nejsou zadány jako volitelné. Atributy informací o volajícím nedělají parametr volitelným. Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán. Hodnoty informací o volajícím jsou vyzařovány jako literály do zprostředkujícího jazyka (IL) v době kompilace. Na rozdíl od <xref:System.Exception.StackTrace%2A> výsledků vlastnosti pro výjimky nejsou ovlivněny obfuskace. Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.

### <a name="member-names"></a>Názvy členů

Atribut můžete `CallerMemberName` použít, abyste se vyhnuli `String` zadání názvu člena jako argumentu volané metody. Pomocí této techniky se vyhnete problému, že **rename refaktoring** nezmění `String` hodnoty. Tato výhoda se hodí zvláště v těchto úlohách:

- Použití trasování a diagnostických rutin.
- Implementace rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> při vazby dat. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez `CallerMemberName` atributu je nutné zadat název vlastnosti jako literál.

Následující graf zobrazuje názvy členů, které `CallerMemberName` jsou vráceny při použití atributu.

|Volání dochází v rámci|Výsledek názvu členu|
|-|-|
|Metoda, vlastnost nebo událost|Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.|
|Konstruktor|Řetězec „.ctor“|
|Statický konstruktor|Řetězec „.cctor“|
|Destruktor|Řetězec „Finalize“|
|Operátory nebo převody definované uživatelem|Vygenerovaný název pro člen, například „op_Addition“.|
|Konstruktor atributu|Název metody nebo vlastnosti, na kterou je atribut použit. Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.|
|Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)|Výchozí hodnota volitelného parametru.|

## <a name="see-also"></a>Viz také

- [Pojmenované a nepovinné argumenty](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [Atributy](../../../standard/attributes/index.md)
