---
title: 'Informace o volajícím (F #)'
description: Popisuje způsob použití atributů Argument informace o volajícím získat informace o volajícím z metody.
ms.date: 04/25/2017
ms.openlocfilehash: 0f2f4b16804d9156d234cc29d1f72ebe80a5b556
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991451"
---
# <a name="caller-information"></a>Informace o volajícím

Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.

Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. V následující tabulce jsou uvedeny atributy informace o volajícím, které jsou definovány v [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) obor názvů:

|Atribut|Popis|Typ|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Název metody nebo vlastnosti volajícího. Dále v tomto tématu v části názvy členů.|`String`|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak můžete použít tyto atributy pro sledování účastníka.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a>Poznámky

Atributy informace o volajícím můžete použít jenom pro volitelné parametry. Je třeba zadat explicitní hodnotu pro každý volitelný parametr. Atributy informace o volajícím způsobit, že kompilátor pro zápis správné hodnoty pro každý volitelný parametr upravené pomocí atributu informace o volajícím.

Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledků [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) pro výjimky, výsledky nejsou ovlivněny obfuskací.

Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.

## <a name="member-names"></a>Názvy členů

Můžete použít [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut vyhnout zadávání názvu členu jako `String` argumentů volané metody. Tímto způsobem se vyhnete problému, která se refaktoring přejmenování nezmění `String` hodnoty. Tato výhoda se hodí zvláště v těchto úlohách:

* Použití trasování a diagnostických rutin.
* Implementace [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) rozhraní při vytvoření vazby mezi daty. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut, musíte zadat název vlastnosti jako literál.

Následující graf ukazuje názvy, které jsou vráceny při použití atributu CallerMemberName členů.

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
