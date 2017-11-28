---
title: "Metody rozšíření (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3db3bc2b213b78ef2dceebcf56c9d5fbfa3016e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods-visual-basic"></a>Metody rozšíření (Visual Basic)
Rozšiřující metody umožňují vývojářům přidání vlastních funkcí k typy dat, které jsou již definováni bez vytvoření nového odvozeného typu. Rozšiřující metody umožňují napíše metoda, kterou lze volat, jako by šlo metodu instance existující typu.  
  
## <a name="remarks"></a>Poznámky  
 Metody rozšíření může být pouze `Sub` postup nebo `Function` postupu. Nelze definovat vlastnost rozšíření, pole nebo událostí. Všechny metody rozšíření musí být označen atributem rozšíření `<Extension()>` z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.  
  
 První parametr v definici – metoda rozšíření určuje, jaký typ dat metoda rozšiřuje. Při spuštění metody první parametr je vázána na instanci typu dat, který vyvolá metodu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu definuje `Print` rozšíření pro <xref:System.String> datového typu. Používá metodu `Console.WriteLine` zobrazíte řetězec. Parametr `Print` metody `aString`, určuje, že metoda rozšiřuje <xref:System.String> třídy.  
  
 [!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Všimněte si, že metoda definice rozšíření je označen atributem rozšíření `<Extension()>`. Označení modul, ve kterém je definovaný metodu je volitelné, ale každá metoda rozšíření musí být označen. <xref:System.Runtime.CompilerServices>musí být importovány pro přístup atribut rozšíření.  
  
 Rozšiřující metody lze deklarovat pouze v rámci moduly. Modul, ve kterém je definovaný rozšiřující metodu obvykle není modul stejný jako ten, ve kterém je volána. Místo toho se importuje modul, který obsahuje metodě rozšíření, pokud je nutné, aby do oboru. Po modul, který obsahuje `Print` je v oboru, lze volat metodu, jako by šlo metodu obyčejnou instance, které nepřijímá žádné argumenty, jako například `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 Další příklad `PrintAndPunctuate`, je také rozšíření <xref:System.String>, tentokrát definovaný s dva parametry. První parametr `aString`, určuje, že metoda rozšíření rozšiřuje <xref:System.String>. Druhý parametr `punc`, měl být řetězec interpunkční znaménka, který je předán v jako argument při volání metody. Metoda zobrazí řetězce, za nímž následuje interpunkčních znamének.  
  
 [!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 Je volána metoda odesláním v argument řetězce pro `punc`:`example.PrintAndPunctuate(".")`  
  
 Následující příklad ukazuje `Print` a `PrintAndPunctuate` definované a volat. <xref:System.Runtime.CompilerServices>v modulu definice se naimportují Chcete-li povolit přístup k atributu rozšíření.  
  
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
  
 Rozšiřující metody jsou v dalším kroku začlenění do oboru a volat.  
  
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
 Všechny možnosti, které je potřeba ji moci spouštět tyto nebo podobné metody rozšíření je, že jejich být v rozsahu. Pokud modul, který obsahuje metody rozšíření nachází v oboru, se zobrazí na IntelliSense a může být volána, jako by šlo metodu obyčejnou instance.  
  
 Všimněte si, že po vyvolání metody se žádný argument se neodesílají prvního parametru. Parametr `aString` v předchozí metoda definice vázán na `example`, instanci `String` , který je volá. Kompilátor použije `example` jako argument posílá první parametr.  
  
 Pokud je volat metody rozšíření pro objekt, který je nastaven na `Nothing`, metody rozšíření. To neplatí obyčejnou metod, které. Můžete zkontrolovat explicitně pro `Nothing` v metodě rozšíření.  
  
## <a name="types-that-can-be-extended"></a>Typy, které lze rozšířit  
 Metody rozšíření můžete definovat na většinu typů, které může být reprezentován v seznamu parametrů jazyka Visual Basic, včetně následujících:  
  
-   Třídy (odkazové typy)  
  
-   Struktury (typy hodnot)  
  
-   Rozhraní  
  
-   Delegáty  
  
-   ByRef a ByVal argumenty  
  
-   Obecná metoda parametry  
  
-   Pole  
  
 Vzhledem k tomu, že první parametr určuje datový typ, který rozšiřuje metodě rozšíření, je vyžadován a nemůže být volitelné. Z tohoto důvodu `Optional` parametry a `ParamArray` parametry nemohou mít první parametr v seznamu parametrů.  
  
 Metody rozšíření nejsou zahrnuty do pozdní vazbu. V následujícím příkladu příkaz `anObject.PrintMe()` vyvolá <xref:System.MissingMemberException> výjimky, bude stejná výjimka se zobrazí, pokud druhý `PrintMe` definice rozšíření metoda byly odstraněny.  
  
 [!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>Doporučené postupy  
 Metody rozšíření poskytují výkonný a pohodlný způsob, jak rozšířit existující typ. Úspěšně používat, jsou ale některé body vzít v úvahu. Tyto aspekty platí především pro autory knihovny tříd, ale mohou ovlivnit všechny aplikace, která používá rozšiřující metody.  
  
 Rozšiřující metody, které přidáte do typy, které nevlastníte jsou nejvíce obecně zranitelnější než rozšiřující metody, které jsou přidány do typy, které řídíte. Existuje řada věcí se může objevit v třídy, které nevlastníte, jež mohou narušit rozšiřující metody.  
  
-   Pokud existuje kteréhokoli člena dostupné instance, které má podpis, který je kompatibilní s argumenty příkazu volání s žádné zužující převody požadované z argument na parametr, metodu instance se použije přednostně libovolné metody rozšíření. Proto pokud přidáte metodu odpovídající instance třídy v určitém okamžiku existujícího člena rozšíření, která závisí na může být nedostupný.  
  
-   Autor metody rozšíření nelze jinými programátory zabránit zápisu konfliktní rozšiřující metody, které může mají přednost před původní přípona.  
  
-   Robustnost lze vylepšit uvedení rozšiřující metody v vlastní obor názvů. Příjemci knihovny potom můžete zahrnout obor názvů nebo vyloučit nebo vyberte mezi obory názvů, odděleně od zbytku knihovny.  
  
-   To může být bezpečnější než je rozšíření třídy, zvlášť pokud nejste vlastníkem rozhraní nebo třída rozšíření rozhraní. Změnu rozhraní ovlivňuje všechny třídy, která implementuje ho. Proto může být Autor méně pravděpodobné, že chcete přidat nebo změnit metody v rozhraní. Ale pokud třída implementuje dvě rozhraní, které mají rozšiřující metody se stejným podpisem, metoda ani rozšíření je viditelný.  
  
-   Většina specifický typ, který můžete rozšiřte. V hierarchii typů Pokud vyberete typ, ze které jsou odvozeny mnoho dalších typů, jsou vrstvy možností, jak zavedení instance metody nebo jiné rozšiřující metody, které může kolidovat s vaším.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Rozšiřující metody, instanci metody a vlastnosti  
 Pokud metoda v oboru instance podpisu, který je kompatibilní s argumenty volání příkazu, metodu instance je zvolen přednostně libovolné metody rozšíření. Metoda instance má vyšší prioritu, i když metoda rozšíření je lepší shodu. V následujícím příkladu `ExampleClass` obsahuje metodu instance s názvem `ExampleMethod` který má jeden parametr typu `Integer`. Metody rozšíření `ExampleMethod` rozšiřuje `ExampleClass`, a má jeden parametr typu `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 První volání `ExampleMethod` v následujícím kódu volá metodu rozšíření, protože `arg1` je `Long` a jsou kompatibilní jenom s `Long` parametr v metodě rozšíření. Druhé volání `ExampleMethod` má `Integer` argument, `arg2`, a volá metodu instance.  
  
 [!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Nyní reverse datové typy parametrů v tyto dvě metody:  
  
 [!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 V tuto chvíli kód v `Main` volá metodu instance obou časy. Důvodem je, že oba `arg1` a `arg2` rozšiřující převod do mají `Long`, a metodu instance má přednost před metodě rozšíření v obou případech.  
  
 [!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 Metody rozšíření proto nelze nahradit existující instance metodu. Když metody rozšíření má stejný název jako metodu instance podpisů nejsou v konfliktu, ale je možné přistupovat obě metody. Například pokud třída `ExampleClass` obsahuje metodu s názvem `ExampleMethod` které nepřijímá žádné argumenty, rozšiřující metody se stejným názvem, ale jiné podpisy jsou povoleny, jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 Výstup z tohoto kódu je následující:  
  
 `Extension method`  
  
 `Instance method`  
  
 Situaci je jednodušší s vlastnostmi: Pokud metody rozšíření má stejný název jako vlastnost třídy ji rozšiřuje, metoda rozšíření není viditelná a není přístupný.  
  
## <a name="extension-method-precedence"></a>Priorita rozšíření – metoda  
 Pokud dvě metody rozšíření, které mají stejné podpisy jsou v oboru a dostupné, jeden s vyšší prioritou bude volána. Metody rozšíření priorita je založena na mechanismu používá k zajištění metodu oboru. V následujícím seznamu jsou přednost hierarchii, postupně od nejvyšší po nejnižší.  
  
1.  Rozšiřující metody definované uvnitř aktuální modul.  
  
2.  Rozšiřující metody definované uvnitř datové typy v aktuálním oboru názvů nebo kterékoli z jeho nadřazených objektů, s podřízené obory názvů s vyšší prioritou než nadřazené obory názvů.  
  
3.  Rozšiřující metody definované uvnitř žádné typ importy v aktuální soubor.  
  
4.  Rozšiřující metody definované uvnitř žádné importy oboru názvů z aktuálního souboru.  
  
5.  Rozšiřující metody definované uvnitř žádné importy typ úrovni projektu.  
  
6.  Rozšiřující metody definované uvnitř žádné importy oboru názvů úrovni projektu.  
  
 Pokud přednost nejednoznačnosti nevyřeší, můžete zadat metodu, která jsou volání plně kvalifikovaný název. Pokud `Print` metoda v předchozím příkladu je definována v modulu s názvem `StringExtensions`, je plně kvalifikovaný název `StringExtensions.Print(example)` místo `example.Print()`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Metody rozšíření](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Module – příkaz](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Volitelné parametry](./optional-parameters.md)  
 [Pole parametrů](./parameter-arrays.md)  
 [Přehled atributy](../../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
