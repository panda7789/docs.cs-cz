---
title: Metody rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 9e005d0dc7da154fbaffbf7e02c55445a1213195
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864335"
---
# <a name="extension-methods-visual-basic"></a>Metody rozšíření (Visual Basic)
Rozšiřující metody umožňují vývojářům přidat vlastní funkce pro datové typy, které jsou již definovány, bez vytváření nového odvozeného typu. Rozšiřující metody umožňují napsat metodu, kterou lze volat jako by šlo metodu instance existujícího typu.  
  
## <a name="remarks"></a>Poznámky  
 Metody rozšíření lze pouze `Sub` procedury nebo `Function` postup. Nelze definovat vlastnost rozšíření, pole nebo události. Všechny metody rozšíření musí být označená pomocí atributu rozšíření `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.  
  
 První parametr v metodě rozšíření určuje, jaký typ dat metoda rozšiřuje. Při spuštění metody je první parametr vázán k instanci datového typu, který vyvolá metodu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad definuje `Print` rozšíření <xref:System.String> datového typu. Metoda používá `Console.WriteLine` pro zobrazení řetězce. Parametr `Print` metody `aString`, stanoví, že metody rozšíří <xref:System.String> třídy.  
  
 [!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]  
  
 Všimněte si, že definice metody rozšíření je označena atributem rozšíření `<Extension()>`. Označení modulu, ve kterém je definována metoda, je volitelný, ale každá metoda rozšíření musí být označeny. <xref:System.Runtime.CompilerServices> musí být importovány pro přístup k atributu rozšíření.  
  
 Metody rozšíření lze deklarovat jen v modulech. Modul, ve kterém je definována rozšiřující metoda obvykle není stejný modul jako ten, ve kterém je volána. Místo toho se importuje modul, který obsahuje metodu rozšíření, pokud musí se jednat o, pro přivedení do rozsahu. Jakmile bude modul obsahující `Print` je v oboru, lze volat metodu, jako by šlo o běžnou metodu instance, která nepřijímá žádné argumenty, jako například `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]  
  
 Následující příklad `PrintAndPunctuate`, je také rozšíření <xref:System.String>, tentokrát definováno se dvěma parametry. První parametr `aString`, stanoví, že metoda rozšíření rozšiřuje <xref:System.String>. Druhý parametr `punc`, je určen jako řetězec interpunkčního, které je předáno jako argument při volání metody. Metoda zobrazí řetězec následovaný interpunkčními znaménky.  
  
 [!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]  
  
 Je volána metoda odesláním v argumentu řetězce pro `punc`: `example.PrintAndPunctuate(".")`  
  
 Následující příklad ukazuje `Print` a `PrintAndPunctuate` definované a volané. <xref:System.Runtime.CompilerServices> je importován v modulu definice Chcete-li povolit přístup k atributu rozšíření.  
  
### <a name="code"></a>Kód  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 V dalším kroku jsou metody rozšíření přeneseny do rozsahu a volá.  
  
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
  
### <a name="comments"></a>Komentáře  
 Všechny možnosti, které je potřeba mít možnost ke spouštění těchto nebo podobných metod rozšíření stačí, aby byly v oboru. Pokud modul, který obsahuje metodu rozšíření se nachází v oboru, je zobrazen v technologii IntelliSense a může být volána, jako by šlo o běžnou metodu instance.  
  
 Všimněte si, že když jsou metody vyvolány, žádný argument se posílá ve pro první parametr. Parametr `aString` v metodě předchozí definice je vázán na `example`, instanci `String` , která je volá. Kompilátor použije `example` jako argument odeslaný na první parametr.  
  
 Pokud rozšiřující metoda je volána pro objekt, který je nastaven `Nothing`, metoda rozšíření se zavolá. To se nevztahuje na běžné metody instancí. Můžete explicitně zjišťovat `Nothing` v metodě rozšíření.  
  
## <a name="types-that-can-be-extended"></a>Typy, které je možné rozšířit  
 Můžete definovat rozšiřující metodu pro většinu typů, které mohou být zastoupeny v seznamu parametrů jazyka Visual Basic, včetně následujících:  
  
- Třídy (typy odkazů)  
  
- Struktury (typy hodnot)  
  
- Rozhraní  
  
- Delegáty  
  
- Argumenty ByRef a ByVal  
  
- Obecné parametry metody  
  
- Pole  
  
 Vzhledem k tomu, že první parametr určuje datový typ, který rozšiřující metoda rozšiřuje, je vyžadován a nemůže být nepovinný. Z tohoto důvodu `Optional` parametry a `ParamArray` parametry nemohou být první parametr v seznamu parametrů.  
  
 Rozšiřující metody nejsou považovány za v pozdní vazbě. V následujícím příkladu příkaz `anObject.PrintMe()` vyvolá <xref:System.MissingMemberException> výjimku, kterou byste viděli stejnou výjimku druhý `PrintMe` definici metody rozšíření se odstranily.  
  
 [!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]  
  
## <a name="best-practices"></a>Doporučené postupy  
 Rozšiřující metody poskytují pohodlný a účinný způsob, jak rozšířit existující typ. Však úspěšně používat, existují některé body ke zvážení. Tyto úvahy platí hlavně pro autory knihoven tříd, ale mohou ovlivnit jakékoli aplikace, které používají rozšiřující metody.  
  
 Obecně jsou zranitelnější než metody rozšíření přidané do typů, které řídíte rozšiřující metody, které přidáte na typy, které nevlastníte. V mnoha může dojít ve třídách, které nevlastníte, jež mohou narušit vaše metody rozšíření.  
  
- Pokud existuje kterýkoli přístupný instanční člen, který má stejný podpis kompatibilní s argumenty v příkazu volání, bez zužujících převodů požadovaných argumentem pro parametr, použije se instanční metoda před jakoukoli metodou rozšíření. Proto pokud metoda příslušné instance je přidána do třídy v určitém okamžiku, existující člen rozšíření, která závisí na může být nepřístupný.  
  
- Autor metody rozšíření nemůže ostatním programátorům zabránit ve vytváření konfliktních metod rozšíření, které mohou mít přednost před původním rozšířením.  
  
- Můžete zlepšit odolnost vložením rozšiřujících metod ve vlastním oboru názvů. Spotřebitelé knihovny potom můžete zahrnout oboru názvů nebo vyloučit nebo volit mezi obory názvů odděleně od zbytku knihovny.  
  
- Může být bezpečnější rozšířit rozhraní než rozšířit třídy, zejména v případě, že není vlastníkem rozhraní nebo třídu. Změna v rozhraní se týká každé třídy, který jej implementuje. Proto že autor bude méně pravděpodobné, že chcete přidat nebo změnit metody v rozhraní. Nicméně pokud třída implementuje dvě rozhraní, které mají stejnou signaturu metody rozšíření, žádná rozšiřující metoda není viditelná.  
  
- Rozšiřte co nejspecifičtější typ., můžete. V hierarchii typů vyberete typ, ze které jsou odvozeny mnoho jiných typů, existují vrstvy možností pro zavedení metody instance nebo jiných rozšiřujících metod, které by mohou narušovat vaše.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Rozšiřující metody, metody Instance a vlastnosti  
 Pokud metoda příslušné instance má podpis, který je kompatibilní s argumenty volání příkazu, metoda instance bude zvolena v preferenci jakoukoli metodou rozšíření. Instanční metoda má přednost, i když rozšiřující metoda představuje lepší shodu. V následujícím příkladu `ExampleClass` obsahuje metodu instance pojmenovanou `ExampleMethod` , který má jeden parametr typu `Integer`. Metoda rozšíření `ExampleMethod` rozšiřuje `ExampleClass`, a má jeden parametr typu `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]  
  
 První volání `ExampleMethod` v následujícím kódu volá metodu rozšíření, protože `arg1` je `Long` a je kompatibilní jenom s `Long` parametr v metodě rozšíření. Druhé volání `ExampleMethod` má `Integer` argument, `arg2`, a volá metodu instance.  
  
 [!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]  
  
 Nyní obraťte datové typy parametrů ve dvou metod:  
  
 [!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]  
  
 Tentokrát kód v `Main` volá metodu instance obou časů. Důvodem je, že oba `arg1` a `arg2` mít rozšiřitelný převod `Long`, a instanční metoda má přednost před metodu rozšíření v obou případech.  
  
 [!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]  
  
 Proto rozšiřující metoda nemůže nahradit stávající metodu instance. Ale když rozšiřující metoda má stejný název jako metoda instance, ale podpisy nejsou v rozporu, obě metody jsou přístupné. Například pokud třída `ExampleClass` obsahuje metodu s názvem `ExampleMethod` , která nebere žádné argumenty, rozšiřující metody se stejným názvem, ale různými podpisy, jsou povoleny, jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]  
  
 Výstup tohoto kódu vypadá takto:  
  
 `Extension method`  
  
 `Instance method`  
  
 Situace je jednodušší s vlastnostmi: Pokud rozšiřující metoda má stejný název jako vlastnost třídy, kterou rozšiřuje, rozšiřující metoda není viditelná a přístupná.  
  
## <a name="extension-method-precedence"></a>Priorita rozšiřující metody  
 Když dvě rozšiřující metody, které mají stejné podpisy jsou v oboru a přístupné, bude vyvolána ta s vyšší prioritou. Přednost metody rozšíření je založena na mechanismu použitém k uvedení metody do oboru. Následující seznam obsahuje hierarchii priority od nejvyšší po nejnižší.  
  
1. Rozšiřující metody definované uvnitř aktuálního modulu.  
  
2. Rozšiřující metody definované uvnitř datových typů v aktuálním oboru názvů, nebo v jednom z jeho rodičů s podřízenými obory názvů mají vyšší prioritu než nadřazené obory názvů.  
  
3. Rozšiřující metody definované uvnitř libovolných importů typu v aktuálním souboru.  
  
4. Rozšiřující metody definované uvnitř libovolných importů oboru názvu v aktuálním souboru.  
  
5. Rozšiřující metody definované uvnitř libovolných importů typu na úrovni projektu.  
  
6. Rozšiřující metody definované uvnitř libovolných importů oboru názvu na úrovni projektu.  
  
 Pokud přednost nevyřeší nejednoznačnosti, můžete určit metodu, kterou voláte plně kvalifikovaný název. Pokud `Print` metoda v předchozím příkladu je definována v modulu s názvem `StringExtensions`, je plně kvalifikovaný název `StringExtensions.Print(example)` místo `example.Print()`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Rozšiřující metody](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Příkaz Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Nepovinné parametry](./optional-parameters.md)
- [Pole parametrů](./parameter-arrays.md)
- [Přehled atributy](../../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
