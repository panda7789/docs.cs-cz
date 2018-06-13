---
title: 'Informace o subjektu volajícím (F #)'
description: Popisuje, jak použít volající informace Argument atributy získat informace o subjektu volajícím z metody.
ms.date: 04/25/2017
ms.openlocfilehash: 6fd80213cdaf2c4662fd4c2ed9eaf8949e397efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564777"
---
# <a name="caller-information"></a>Informace o subjektu volajícím

Pomocí atributů Informace o volajícím můžete získat informace o volajícím metody. Můžete získat cestu k souboru zdrojového kódu, číslo řádku ve zdrojovém kódu a název členu volajícího. Tyto informace jsou užitečné pro trasování, ladění a vytváření diagnostických nástrojů.

Pro získání těchto informací můžete použít atributy, které jsou použity na volitelné parametry, z nichž každý má výchozí hodnotu. Následující tabulka uvádí informace o volajícím atributy, které jsou definovány v [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) obor názvů:

|Atribut|Popis|Typ|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Úplná cesta zdrojového souboru, který obsahuje volajícího. Toto je cesta k souboru v době kompilace.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Číslo řádku ve zdrojovém souboru, ve kterém je volána metoda.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Název metody nebo vlastnosti volajícího. Najdete v části názvy členů později v tomto tématu.|`String`|

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak můžete pomocí těchto atributů pro trasování volající.

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

Atributy s informacemi volající je použít jenom pro volitelné parametry. Je třeba zadat explicitní hodnotu pro každý volitelný parametr. Informace o volajícím atributy způsobit kompilátoru pro zápis správné hodnoty pro každý volitelný parametr dekorované s atributem volající informace.

Hodnoty atributů Informace o volajícím jsou emitovány jako literály do jazyka Intermediate Language (IL) v době kompilace. Na rozdíl od výsledky [trasování zásobníku](/dotnet/api/system.diagnostics.stacktrace) maskováním nemá vliv vlastnost pro výjimky, výsledky.

Volitelné argumenty můžete explicitně zadat, chcete-li řídit nebo skrýt informace o volajícím.

## <a name="member-names"></a>Názvy členů

Můžete použít [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut Vyhněte se zadání název člena jako `String` argument volané metodě. Pomocí tohoto postupu se vyhnout problém, který přejmenovat refaktoring nezmění `String` hodnoty. Tato výhoda se hodí zvláště v těchto úlohách:

* Použití trasování a diagnostických rutin.
* Implementace [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) rozhraní při vytváření vazby data. Toto rozhraní umožňuje vlastnosti objektu oznámit vázanému ovládacímu prvku, že došlo ke změně vlastnosti, aby ovládací prvek mohl zobrazit aktualizované informace. Bez [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) atribut, musíte zadat název vlastnosti jako literál.

Následující graf zobrazuje názvy, které jsou vráceny při použití atributu CallerMemberName člena.

|K volání dochází v rámci|Výsledek názvu členu|
|-------------------|------------------|
|Metoda, vlastnost nebo událost|Název metody, vlastnosti nebo události, z nichž bylo volání provedeno.|
|Konstruktor|Řetězec „.ctor“|
|Statický konstruktor|Řetězec „.cctor“|
|Destruktor|Řetězec „Finalize“|
|Operátory nebo převody definované uživatelem|Vygenerovaný název pro člen, například „op_Addition“.|
|Konstruktor atributu|Název členu, na který se atribut používá. Pokud je atribut libovolný prvek v členu (například parametr, návratová hodnota nebo parametr obecného typu), je tento výsledek názvem členu, který je přidružen k tomuto prvku.|
|Žádný obsahující člen (například úroveň sestavení nebo atributy, které jsou použity na typy)|Výchozí hodnota volitelného parametru.|

## <a name="see-also"></a>Viz také
 [Atributy](attributes.md)  
 [Pojmenované argumenty](parameters-and-arguments.md#named-arguments)  
 [Volitelné parametry](parameters-and-arguments.md#optional-parameters)  
