---
title: Anonymní typy (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 451fe45c9b5efbeb64b1066d6ba8e5f9b27300c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-types-visual-basic"></a>Anonymní typy (Visual Basic)
Visual Basic podporuje anonymní typy, které vám umožní vytvořit objekty bez nutnosti psaní definice třídy pro datový typ. Kompilátor místo, vygeneruje třídu pro vás. Třída nemá žádný použitelný název, dědí přímo z <xref:System.Object>a obsahuje vlastnosti, které zadáte v deklarace objektu. Protože není určen název typu dat, se odkazuje jako *anonymního typu*.  
  
 Následující příklad deklaruje a vytvoří proměnnou `product` jako instanci anonymního typu, která má dvě vlastnosti `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 A *dotaz výrazu* používá anonymní typy kombinovat sloupce dat, vybrané dotazu. Typ výsledku nelze definovat předem, protože nelze předpovědět sloupce, které může vybrat konkrétní dotaz. Anonymní typy umožňují vytvořit dotaz, který vybere libovolný počet sloupců v libovolném pořadí. Kompilátor vytvoří datový typ, který odpovídá zadané vlastnosti a zadaném pořadí.  
  
 V následujících příkladech `products` je seznam objekty produktu, z nichž každý má mnoho vlastností. Proměnné `namePriceQuery` obsahuje definici dotazu, který při spuštění, vrátí kolekci instancí anonymního typu, která má dvě vlastnosti `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 Proměnné `nameQuantityQuery` obsahuje definici dotazu, který při spuštění, vrátí kolekci instancí anonymního typu, která má dvě vlastnosti `Name` a `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 Další informace o kódu vytvořené kompilátoru pro anonymní typ najdete v tématu [anonymní definice typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Název typu anonymní je kompilátoru generované a se může lišit od kompilace kompilace. Váš kód by neměl používat nebo spoléhají na název anonymního typu, protože název mohou změnit, když na projekt znovu zkompiluje.  
  
## <a name="declaring-an-anonymous-type"></a>Anonymní typ deklarace  
 Prohlášení o instanci anonymního typu používá inicializátoru seznamu k určení vlastností typu. Zadávat lze pouze vlastnosti a při deklaraci anonymního typu, není dalších prvků třídy například metody nebo události. V následujícím příkladu `product1` představuje instanci anonymního typu, která má dvě vlastnosti: `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 Je-li určit vlastnosti jako vlastnosti klíče, můžete je použít k porovnání rovnost obou instancí anonymního typu. Hodnoty vlastnosti klíče však nelze změnit. Najdete v části vlastnosti klíče později v tomto tématu pro další informace.  
  
 Všimněte si, že deklarace instanci anonymního typu jako deklarace instanci s názvem typu pomocí inicializátoru objektu:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 Další informace o jiných způsobech k určení vlastností anonymního typu najdete v tématu [postupy: odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti se liší od neklíčovými vlastnostmi základní způsoby:  
  
-   Aby bylo možné zjistit, zda jsou dvě instance stejné jsou porovnávány pouze hodnoty vlastnosti klíče.  
  
-   Hodnoty vlastnosti klíče jen pro čtení a nedá se změnit.  
  
-   Jenom klíčové vlastnosti hodnoty jsou součástí algoritmus hash generované kompilátorem kód pro anonymní typ.  
  
### <a name="equality"></a>Rovnost  
 Instance anonymní typy může být stejná, pouze pokud jsou instance stejného typu anonymní. Kompilátor dvě instance považuje za instance stejného typu, pokud nebudou splňovat následující podmínky:  
  
-   Jsou deklarovány ve stejném sestavení.  
  
-   Jejich vlastnosti se stejnými názvy stejné odvozené typy a jsou deklarovány ve stejném pořadí. Název porovnání nerozlišují malá a velká písmena.  
  
-   Stejné vlastnosti v každé jsou označeny jako vlastnosti klíče.  
  
-   Minimálně jedna vlastnost v každé deklaraci je klíčovou vlastnost.  
  
 Instanci anonymní typy, která nemá žádné klíčové vlastnosti rovná pouze na sebe sama.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 Dvě instance stejného typu anonymní jsou stejné, pokud hodnoty vlastnosti jejich klíče jsou stejné. Následující příklady znázorňují, jak je testován rovnosti.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a>Jen pro čtení hodnoty  
 Hodnoty vlastnosti klíče nelze změnit. Například v `prod8` v předchozím příkladu `Name` a `Price` pole jsou `read-only`, ale `OnHand` lze změnit.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Anonymní typy z výrazy dotazů  
 Výrazy dotazů vždy nevyžadují vytvoření anonymní typy. Pokud je to možné, používají existující typ pro uložení dat sloupců. K tomu dochází, pokud dotaz vrátí buď celý záznamy ze zdroje dat, nebo pouze jedno pole z každý záznam. Následující příklady kódu `customers` je kolekce objektů `Customer` třídy. Třída má mnoho vlastností a nejméně jeden z nich můžete zahrnout do výsledku dotazu v libovolném pořadí. V první dva příklady jsou vyžadovány žádné anonymní typy, protože dotazy vybrat elementy typů s názvem:  
  
-   `custs1` obsahuje kolekci řetězce, protože `cust.Name` je řetězec.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2` obsahuje kolekci `Customer` objekty, protože každý element `customers` je `Customer` objektu a celého elementu je vybrána v dotazu.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 Nicméně odpovídající pojmenované typy nejsou vždy k dispozici. Můžete vybrat zákazníka názvy a adresy pro jediný účel, ID zákazníka a umístění pro jinou a jména zákazníků, adresy a pořadí historií třetí. Anonymní typy umožňuje vybrat libovolnou kombinaci vlastností v libovolném pořadí, bez první deklarace nového typu s názvem pro uložení výsledek. Kompilátor místo toho vytvoří anonymní typ pro každý kompilace vlastnosti. Následující dotaz vybere pouze zákazníka název a číslo ID z každé `Customer` objekt v `customers`. Proto kompilátor vytvoří instanci anonymního typu, který obsahuje pouze tyto dvě vlastnosti.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 Názvy a datové typy vlastností v anonymního typu jsou převzaty z argumenty, které mají `Select`, `cust.Name` a `cust.ID`. Vlastnosti v anonymní typ, který je vytvořen pomocí dotazu jsou vždy klíčové vlastnosti. Když `custs3` se spustí v následujícím `For Each` ve smyčce, výsledkem je kolekce instancí anonymní typ s dvě klíčové vlastnosti, `Name` a `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 Elementy v kolekci reprezentována `custs3` jsou silného typu, a můžete IntelliSense procházet dostupné vlastnosti a jejich typy ověření.  
  
 Další informace najdete v tématu [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Rozhodování, jestli se má použít anonymní typy  
 Než vytvoříte objekt jako instanci anonymní třídy, zvažte, zda je to nejlepší možnost. Například pokud chcete vytvořit dočasný objekt tak, aby obsahovala související data a máte není nutné pro další pole a metody, které může obsahovat úplné třídy, anonymní typ je dobrým řešením. Anonymní typy jsou také vhodné, pokud chcete použít jiný výběr vlastnosti pro každý deklarace, nebo pokud chcete změnit pořadí vlastnosti. Ale pokud projekt obsahuje několik objektů, které mají stejné vlastnosti v pevném pořadí, je lze deklarovat snadněji pomocí konstruktoru třídy s názvem typu. Například s odpovídající konstruktor, aby bylo jednodušší deklarovat několik instancí `Product` třídy, než se dá deklarovat několik instancí anonymního typu.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 Další výhodou pojmenované typy je, že můžete kompilátor catch náhodnému chybným zadáním názvu vlastnosti. V předchozích příkladech `firstProd2`, `secondProd2`, a `thirdProd2` by měla být instance stejného typu anonymní. Ale pokud byste chtěli omylem deklarovat `thirdProd2` v jednom z následujících způsobů, bude jeho typ z `firstProd2` a `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 Je důležité existují omezení na stránce použít anonymní typy, které se nevztahují na instance pojmenované typy. `firstProd2`, `secondProd2`, a `thirdProd2` jsou instance stejného typu anonymní. Název sdílené anonymního typu však není k dispozici a nelze vložit, kde je očekávána název typu ve vašem kódu. Například anonymní typ nelze použít k definování podpis metody, deklarace jiné proměnné nebo pole nebo v jakékoli deklaraci typu. Anonymní typy v důsledku toho nejsou vhodné, když máte sdílet informace přes metody.  
  
## <a name="an-anonymous-type-definition"></a>Definice autonomního typu  
 V reakci na deklaraci instanci anonymního typu kompilátor vytvoří nové definice třídy, která obsahuje zadané vlastnosti.  
  
 Pokud anonymní typ obsahuje alespoň jednu klíčovou vlastnost, definice nahradí tři členy zděděno z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>. Kód vrácená pro testování rovnosti a určení, že hodnota hash kód považovat jenom klíčové vlastnosti. Pokud anonymní typ obsahuje žádné klíčové vlastnosti, pouze <xref:System.Object.ToString%2A> přepsána. Explicitně pojmenované vlastnosti anonymního typu nelze v konfliktu s tyto generovaného metody. To znamená, že nelze použít `.Equals`, `.GetHashCode`, nebo `.ToString` na název vlastnosti.  
  
 Definice autonomního typu, které mají alespoň jednu klíče vlastnost také implementace <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, kde `T` je typ anonymního typu.  
  
 Další informace o kódu vytvořené kompilátor a funkci přepsaného metod najdete v tématu [anonymní definice typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Viz také  
 [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)
