---
title: Informace o volajícím
description: Popisuje způsob použití atributů argumentu informace o volajícím k získání informací o volajícím z metody.
ms.date: 04/25/2017
ms.openlocfilehash: e7bbc3830a95bd25cfc2fb369b204d367b775815
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106583"
---
# <a name="caller-information"></a>Informace o volajícím

Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.

Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. V následující tabulce jsou uvedeny atributy informací o volajícím, které jsou definovány v oboru názvů [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :

|Atribut|Popis|type|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Název metody nebo vlastnosti volajícího. Viz část názvy členů dále v tomto tématu.|`String`|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak můžete tyto atributy použít k trasování volajícího.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>Poznámky

Atributy informací o volajícím se dají použít jenom u volitelných parametrů. Atributy informace o volajícím způsobí, že kompilátor zapíše správnou hodnotu pro každý volitelný parametr upravený pomocí atributu info volajícího.

Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledků vlastnosti [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) pro výjimky nejsou výsledky ovlivněny zmatením.

Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.

## <a name="member-names"></a>Názvy členů

[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) Atribut lze použít k zamezení zadání názvu člena `String` jako argumentu volané metody. Pomocí této techniky se vyhnete problému s tím, že Refaktoring přejmenování `String` hodnoty nemění. Tato výhoda se hodí zvláště v těchto úlohách:

- Použití trasování a diagnostických rutin.
- Implementace rozhraní [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) při vázání dat Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) Bez atributu je nutné zadat název vlastnosti jako literál.

Následující graf znázorňuje názvy členů, které jsou vráceny při použití atributu CallerMemberName.

|K volání dochází v rámci|Výsledek názvu členu|
|-------------------|------------------|
|Metoda, vlastnost nebo událost|Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.|
|Konstruktor|Řetězec „.ctor“|
|Statický konstruktor|Řetězec „.cctor“|
|Destruktor|Řetězec „Finalize“|
|Operátory nebo převody definované uživatelem|Vygenerovaný název pro člen, například „op_Addition“.|
|Konstruktor atributu|Název členu, na který se atribut používá. Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.|
|Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)|Výchozí hodnota volitelného parametru.|

## <a name="see-also"></a>Viz také:

- [Atributy](attributes.md)
- [Pojmenované argumenty](parameters-and-arguments.md#named-arguments)
- [Volitelné parametry](parameters-and-arguments.md#optional-parameters)
