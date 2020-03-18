---
title: Informace o volajícím (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595349"
---
# <a name="caller-information-c"></a>Informace o volajícím (C#)

Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.

Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. V následující tabulce jsou uvedeny atributy <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> Informace o volajícím, které jsou definovány v oboru názvů:

|Atribut|Popis|Typ|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti volajícího. Viz [Jména členů](#member-names) dále v tomto tématu.|`String`|

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití atributů Informace o volajícím. Při každém volání `TraceMessage` metody informace o volajícím je nahrazen jako argumenty volitelné parametry.

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
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a>Poznámky

Pro každý volitelný parametr je třeba zadat explicitní výchozí hodnotu. Atributy Informace o volajícím nelze použít u parametrů, které nejsou uvedeny jako volitelné.

Atributy Informace o volajícím neučiní parametr volitelným. Místo toho mají vliv na výchozí hodnotu, která je předána, pokud je argument vynechán.

Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od <xref:System.Exception.StackTrace%2A> výsledků vlastnosti pro výjimky nejsou ovlivněny obfuskace.

Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.

### <a name="member-names"></a>Názvy členů

Atribut můžete `CallerMemberName` použít, abyste se vyhnuli `String` zadání názvu člena jako argumentu volané metody. Pomocí této techniky se vyhnete problému, že **rename refaktoring** nezmění `String` hodnoty. Tato výhoda se hodí zvláště v těchto úlohách:

- Použití trasování a diagnostických rutin.

- Implementace rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> při vazby dat. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez `CallerMemberName` atributu je nutné zadat název vlastnosti jako literál.

Následující graf zobrazuje názvy členů, které `CallerMemberName` jsou vráceny při použití atributu.

|K volání dochází v rámci|Výsledek názvu členu|
|-|-|
|Metoda, vlastnost nebo událost|Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.|
|Konstruktor|Řetězec „.ctor“|
|Statický konstruktor|Řetězec „.cctor“|
|Destruktor|Řetězec „Finalize“|
|Operátory nebo převody definované uživatelem|Vygenerovaný název pro člen, například „op_Addition“.|
|Konstruktor atributu|Název metody nebo vlastnosti, na kterou je atribut použit. Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.|
|Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)|Výchozí hodnota volitelného parametru.|

## <a name="see-also"></a>Viz také

- [Atributy (C#)](./attributes/index.md)
- [Běžné atributy (C#)](./attributes/common-attributes.md)
- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Koncepty programování (C#)](./index.md)
