---
title: Rozšiřující metody
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: a88756fce9137f89db1b6b8b007d528e98381830
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341179"
---
# <a name="extension-methods-visual-basic"></a>Metody rozšíření (Visual Basic)

Metody rozšíření umožňují vývojářům přidat vlastní funkce k datovým typům, které jsou již definovány bez vytváření nového odvozeného typu. Rozšiřující metody umožňují napsat metodu, která může být volána, jako by šlo o metodu instance existujícího typu.

## <a name="remarks"></a>Poznámky

Metoda rozšíření může být pouze `Sub` procedura nebo procedura `Function`. Nelze definovat vlastnost rozšíření, pole nebo událost. Všechny metody rozšíření musí být označené atributem rozšíření `<Extension>` z oboru názvů <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> a musí být definované v [modulu](../../../language-reference/statements/module-statement.md). Pokud je metoda rozšíření definována mimo modul, Visual Basic kompilátor vygeneruje chybu [BC36551](../../../misc/bc36551.md), "metody rozšíření mohou být definovány pouze v modulech".

První parametr v definici metody rozšíření určuje, který typ dat metoda rozšiřuje. Při spuštění metody je první parametr svázán s instancí datového typu, který vyvolá metodu.

Atribut `Extension` lze použít pouze pro Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)nebo [`Function`](../../../language-reference/statements/function-statement.md). Pokud ji použijete pro `Class` nebo `Structure`, kompilátor Visual Basic vygeneruje chybu [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), atribut Extension lze použít pouze pro ' Module ', ' sub ' nebo ' function ' deklarací.

## <a name="example"></a>Příklad

Následující příklad definuje rozšíření `Print` pro datový typ <xref:System.String>. Metoda používá `Console.WriteLine` k zobrazení řetězce. Parametr metody `Print`, `aString`, stanoví, že metoda rozšiřuje třídu <xref:System.String>.

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

Všimněte si, že definice rozšiřující metody je označena atributem rozšíření `<Extension()>`. Označení modulu, ve kterém je metoda definovaná, je volitelné, ale každá metoda rozšíření musí být označená. aby bylo možné získat přístup k atributu rozšíření, je třeba importovat <xref:System.Runtime.CompilerServices>.

Metody rozšíření mohou být deklarovány pouze v rámci modulů. Modul, ve kterém je definována metoda rozšíření, obvykle není stejný modul jako ten, ve kterém je volána. Místo toho je importován modul, který obsahuje metodu rozšíření, pokud je potřeba, aby se přenesl do rozsahu. Po modulu, který obsahuje `Print` v oboru, může být metoda volána, jako by šlo o běžnou metodu instance, která nepřijímá žádné argumenty, jako je například `ToUpper`:

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

Další příklad, `PrintAndPunctuate`, je také rozšíření pro <xref:System.String>, tentokrát definováno se dvěma parametry. První parametr `aString`stanoví, že rozšiřující metoda rozšiřuje <xref:System.String>. Druhý parametr, `punc`, má být řetězec interpunkční znaménka, která je předána jako argument při volání metody. Metoda zobrazí řetězec následovaný interpunkční znaménky.

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

Metoda je volána při odeslání do řetězcového argumentu pro `punc`: `example.PrintAndPunctuate(".")`

Následující příklad ukazuje `Print` a `PrintAndPunctuate` definovány a volány. <xref:System.Runtime.CompilerServices> je importován v modulu definice, aby bylo možné povolit přístup k atributu rozšíření.

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

Dále se rozšiřující metody přenesou do rozsahu a nazývají se:

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

Vše, co musí být schopné spustit tyto nebo podobné metody rozšíření, je, že jsou v oboru. Pokud je modul obsahující metodu rozšíření v oboru, je viditelný v technologii IntelliSense a může být volána, jako by šlo o běžnou metodu instance.

Všimněte si, že při vyvolání metod není v parametru pro první parametr odeslán žádný argument. Parametr `aString` v předchozích definicích metod je vázán na `example`, instance `String`, která je volá. Kompilátor použije `example` jako argument odeslaný do prvního parametru.

Pokud je volána metoda rozšíření pro objekt, který je nastaven na `Nothing`, spustí se metoda rozšíření. To se nevztahuje na běžné metody instance. Můžete explicitně vyhledat `Nothing` v metodě rozšíření.

## <a name="types-that-can-be-extended"></a>Typy, které lze rozšířit

Můžete definovat metodu rozšíření pro většinu typů, které mohou být reprezentovány v seznamu parametrů Visual Basic, včetně následujících:

- Třídy (typy odkazů)
- Struktury (typy hodnot)
- Rozhraní
- Delegáti
- Argumenty ByRef a ByVal
- Parametry obecné metody
- Pole

Vzhledem k tomu, že první parametr určuje datový typ, který rozšiřující metoda rozšiřuje, je požadován a nemůže být volitelný. Z tohoto důvodu parametry `Optional` parametrů a `ParamArray` parametrů nemohou být prvním parametrem v seznamu parametrů.

Metody rozšíření nejsou v pozdní vazbě zvažovány. V následujícím příkladu příkaz `anObject.PrintMe()` vyvolá výjimku <xref:System.MissingMemberException>, stejná výjimka, jakou byste viděli, pokud byla odstraněna druhá definice metody rozšíření `PrintMe`.

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a>Osvědčené postupy

Metody rozšíření poskytují pohodlný a účinný způsob, jak rozšířit existující typ. Pokud je však chcete úspěšně použít, je třeba vzít v úvahu několik bodů. Tyto požadavky platí hlavně pro autory knihoven tříd, ale mohou ovlivnit jakoukoli aplikaci, která používá metody rozšíření.

Obecně platí, že metody rozšíření, které přidáte do typů, které nevlastníte, jsou zranitelnější než metody rozšíření přidané do typů, které ovládáte. Ve třídách, které nevlastníte, může dojít k několika akcím, které mohou narušovat vaše metody rozšíření.

- Pokud existuje nějaký přístupný člen instance, který má signaturu kompatibilní s argumenty v příkazu volání, bez zúžení převodů vyžadovaných v argumentu pro parametr, metoda instance bude použita v preference pro jakoukoliv metodu rozšíření. Proto pokud je příslušná metoda instance přidána do třídy v nějakém okamžiku, existující člen rozšíření, ke kterému jste se spoléhali, může být nepřístupný.

- Autor metody rozšíření nemůže zabránit jiným programátorům v zápisu konfliktních metod rozšíření, které mohou mít přednost před původním rozšířením.

- Můžete zvýšit odolnost tím, že umístíte rozšiřující metody do svého vlastního oboru názvů. Příjemci vaší knihovny mohou potom zahrnout obor názvů nebo vyloučit z něj nebo vybrat mezi obory názvů odděleně od ostatních knihoven.

- Může být bezpečnější pro rozšiřování rozhraní, než je rozšiřování tříd, zejména v případě, že nevlastníte rozhraní nebo třídu. Změna rozhraní má vliv na každou třídu, která ji implementuje. Proto může být autor méně pravděpodobný přidat nebo změnit metody v rozhraní. Nicméně pokud třída implementuje dvě rozhraní, která mají metody rozšíření se stejnou signaturou, není žádná metoda rozšíření viditelná.

- Zvětšete konkrétní typ, který můžete. Pokud v hierarchii typů vyberete typ, ze kterého je odvozeno mnoho dalších typů, existují různé úrovně možností pro zavedení instančních metod nebo jiných rozšiřujících metod, které mohou kolidovat s vámi.

## <a name="extension-methods-instance-methods-and-properties"></a>Metody rozšíření, metody instance a vlastnosti

Pokud má metoda instance v rámci oboru signaturu, která je kompatibilní s argumenty volání příkazu, je metoda instance zvolena v předvolbách libovolné metodě rozšíření. Metoda instance má přednost, i když je rozšiřující metoda lepší shoda. V následujícím příkladu `ExampleClass` obsahuje metodu instance s názvem `ExampleMethod`, která má jeden parametr typu `Integer`. Metoda rozšíření `ExampleMethod` rozšiřuje `ExampleClass`a má jeden parametr typu `Long`.

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

První volání `ExampleMethod` v následujícím kódu volá metodu rozšíření, protože `arg1` je `Long` a je kompatibilní pouze s parametrem `Long` v metodě rozšíření. Druhé volání `ExampleMethod` má argument `Integer`, `arg2`a volá metodu instance.

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

Nyní obrátíte datové typy parametrů ze dvou metod:

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

Tentokrát kód v `Main` volá metodu instance obě časy. Důvodem je, že `arg1` i `arg2` mají rozšiřující převod na `Long`a metoda instance má v obou případech přednost před metodou rozšíření.

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

Proto metoda rozšíření nemůže nahradit existující metodu instance. Nicméně, pokud má metoda rozšíření stejný název jako metoda instance, ale signatury nekolidují, obě metody jsou k dispozici. Například pokud třída `ExampleClass` obsahuje metodu s názvem `ExampleMethod`, která nepřijímá žádné argumenty, metody rozšíření se stejným názvem, ale různé podpisy jsou povoleny, jak je znázorněno v následujícím kódu.

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

Výstup z tohoto kódu je následující:

```console
Extension method
Instance method
```

Tato situace je jednodušší s vlastnostmi: Pokud má rozšiřující metoda stejný název jako vlastnost třídy, kterou rozšiřuje, není metoda rozšíření viditelná a nelze k ní mít přístup.

## <a name="extension-method-precedence"></a>Priorita metody rozšíření

V případě, že dvě metody rozšíření, které mají stejné signatury, jsou v oboru a přístupné, bude vyvolána ta s vyšší prioritou. Priorita metody rozšíření je založena na mechanismu, který je použit k převedení metody do rozsahu. Následující seznam zobrazuje hierarchii priority od nejvyšší po nejnižší.

1. Metody rozšíření definované v aktuálním modulu.

2. Rozšiřující metody definované uvnitř datových typů v aktuálním oboru názvů nebo kterémkoli z jeho nadřazených objektů s podřízenými obory názvů s vyšší prioritou než nadřazené obory názvů.

3. Rozšiřující metody definované uvnitř libovolných importů typu v aktuálním souboru.

4. Rozšiřující metody definované uvnitř libovolných importů oboru názvů v aktuálním souboru.

5. Rozšiřující metody definované uvnitř všech importů typu na úrovni projektu.

6. Rozšiřující metody definované uvnitř libovolných importů oboru názvů na úrovni projektu.

Pokud priorita nejednoznačnosti nevyřeší, můžete použít plně kvalifikovaný název k určení volané metody. Je-li metoda `Print` v předchozím příkladu definována v modulu s názvem `StringExtensions`, je plně kvalifikovaný název `StringExtensions.Print(example)` místo `example.Print()`.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Příkaz Module](../../../language-reference/statements/module-statement.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Nepovinné parametry](optional-parameters.md)
- [Pole parametrů](parameter-arrays.md)
- [Přehled atributů](../../concepts/attributes/index.md)
- [Obor v Visual Basic](../declared-elements/scope.md)
