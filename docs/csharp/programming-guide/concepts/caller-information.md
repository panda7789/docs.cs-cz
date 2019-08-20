---
title: Informace o volajícím (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595349"
---
# <a name="caller-information-c"></a>Informace o volajícím (C#)

Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.

Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> definovány v oboru názvů:

|Atribut|Popis|type|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Název metody nebo vlastnosti volajícího. Viz [názvy členů](#member-names) dále v tomto tématu.|`String`|

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití atributů Informace o volajícím. Při každém volání `TraceMessage` metody jsou informace o volajícím nahrazeny jako argumenty nepovinných parametrů.

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

Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledků <xref:System.Exception.StackTrace%2A> vlastnosti pro výjimky nejsou výsledky ovlivněny zmatením.

Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.

### <a name="member-names"></a>Názvy členů

`CallerMemberName` Atribut lze použít k zamezení zadání názvu člena `String` jako argumentu volané metody. Pomocí této techniky se vyhnete problému s tím, že refaktoring **přejmenování** `String` hodnoty nemění. Tato výhoda se hodí zvláště v těchto úlohách:

- Použití trasování a diagnostických rutin.

- <xref:System.ComponentModel.INotifyPropertyChanged> Implementace rozhraní při vázání dat. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. `CallerMemberName` Bez atributu je nutné zadat název vlastnosti jako literál.

Následující graf znázorňuje názvy členů, které jsou vráceny při použití `CallerMemberName` atributu.

|K volání dochází v rámci|Výsledek názvu členu|
|-|-|
|Metoda, vlastnost nebo událost|Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.|
|Konstruktor|Řetězec „.ctor“|
|Statický konstruktor|Řetězec „.cctor“|
|Destruktor|Řetězec „Finalize“|
|Operátory nebo převody definované uživatelem|Vygenerovaný název pro člen, například „op_Addition“.|
|Konstruktor atributu|Název metody nebo vlastnosti, na kterou je atribut použit. Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.|
|Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)|Výchozí hodnota volitelného parametru.|

## <a name="see-also"></a>Viz také:

- [Atributy (C#)](./attributes/index.md)
- [Společné atributy (C#)](./attributes/common-attributes.md)
- [Pojmenované a nepovinné argumenty](../classes-and-structs/named-and-optional-arguments.md)
- [Koncepty programování (C#)](./index.md)
