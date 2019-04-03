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
ms.openlocfilehash: 3dc2083e5b4fd06250a1387c32f0eba28e879b30
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829132"
---
# <a name="anonymous-types-visual-basic"></a>Anonymní typy (Visual Basic)
Visual Basic podporuje anonymní typy, které vám umožní vytvářet objekty bez psaní definice třídy datového typu. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název, dědí přímo z <xref:System.Object>a obsahuje vlastnosti, které jste zadali v rámci deklarace objektu. Protože není zadán název datového typu, to se označuje jako *anonymního typu*.  
  
 Následující příklad deklaruje a vytvoří proměnnou `product` jako instanci anonymního typu, který má dvě vlastnosti `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 A *výrazu dotazu* používá anonymní typy zkombinovat sloupce dat vybraných v dotazu. Typ výsledku nelze definovat předem, protože nelze předvídat sloupce, které může vybrat konkrétní dotaz. Anonymní typy umožňují napsat dotaz, který vybere libovolný počet sloupců, v libovolném pořadí. Kompilátor vytvoří datový typ, který odpovídá zadané vlastnosti a v uvedeném pořadí.  
  
 V následujících příkladech `products` je seznam produktů objektů, z nichž každý má mnoho vlastností. Proměnné `namePriceQuery` obsahuje definici dotazu, který, pokud je spuštěn, vrátí kolekci instancí anonymního typu, který má dvě vlastnosti, `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 Proměnné `nameQuantityQuery` obsahuje definici dotazu, který, pokud je spuštěn, vrátí kolekci instancí anonymního typu, který má dvě vlastnosti, `Name` a `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Další informace o kód vytvořený kompilátorem pro anonymní typ, naleznete v tématu [definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  Název anonymního typu je kompilátor vygeneruje a se může lišit od kompilace do kompilace. Váš kód by neměl používat nebo využívají název anonymního typu, protože název se může změnit při nové kompilaci projektu.  
  
## <a name="declaring-an-anonymous-type"></a>Deklarace anonymního typu  
 Deklarace instanci anonymního typu pomocí seznamu inicializátorů určuje vlastnosti typu. Při deklaraci anonymního typu, nikoli další prvky třídy například metody nebo události, můžete určit pouze vlastnosti. V následujícím příkladu `product1` představuje instanci anonymního typu, který má dvě vlastnosti: `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Je-li určit vlastnosti jako vlastnosti klíče je můžete použít k porovnání rovnost obou instancí anonymního typu. Však hodnoty vlastnosti klíče nelze změnit. Dále v tomto tématu pro další informace v části vlastnosti klíče.  
  
 Všimněte si, že deklarace instanci anonymního typu je třeba deklarovat pomocí inicializátoru objektu instanci s názvem typu:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Další informace o dalších způsobech určit vlastnosti anonymního typu najdete v tématu [jak: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Vlastnosti klíče  
 Vlastnosti klíče lišit od vlastnosti neklíčovým základní způsoby:  
  
-   Aby bylo možné zjistit, zda jsou dvě instance rovnocenné jsou porovnány pouze hodnoty vlastnosti klíče.  
  
-   Hodnoty vlastnosti klíče jsou jen pro čtení a nedá se změnit.  
  
-   Pouze hodnoty vlastností klíče jsou součástí kód generovaný kompilátorem hashovací algoritmus pro anonymního typu.  
  
### <a name="equality"></a>Rovnost  
 Instance anonymních typů může být rovny, pouze pokud jsou instancemi stejného anonymního typu. Kompilátor zpracovává dvě instance jako instance stejného typu, pokud nebudou splňovat následující podmínky:  
  
-   Jsou deklarovány ve stejném sestavení.  
  
-   Jejich vlastnosti mají stejné názvy, stejné odvozené typy a jsou deklarovány ve stejném pořadí. Název porovnání nerozlišují malá a velká písmena.  
  
-   Stejné vlastnosti v každém jsou označeny jako vlastnosti klíče.  
  
-   Alespoň jednu vlastnost v deklaraci je klíčovou vlastnost.  
  
 Instance anonymních typů, která nemá žádné klíčové vlastnosti rovná pouze na sebe sama.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Dva výskyty stejného anonymního typu jsou si rovny, pokud hodnoty jejich klíče vlastnosti jsou stejné. Následující příklady znázorňují, jak testovat rovnost.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Hodnoty jen pro čtení  
 Nelze změnit hodnoty vlastnosti klíče. Například v `prod8` v předchozím příkladu `Name` a `Price` pole jsou `read-only`, ale `OnHand` lze změnit.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Anonymní typy z – výrazy dotazů  
 Výrazy dotazu není vždy třídou vyžadována vytváření anonymních typů. Pokud je to možné, používají k uložení dat sloupce existujícího typu. K tomu dojde, když dotaz vrátí buď celých záznamů ze zdroje dat, nebo pouze jedno pole z každého záznamu. V následujících příkladech kódu `customers` je kolekce objektů `Customer` třídy. Třída má mnoho vlastností a může obsahovat jeden nebo více z nich ve výsledku dotazu v libovolném pořadí. V první dva příklady jsou vyžadovány žádné anonymní typy, protože dotazů vyberte elementů pojmenovaných typů:  
  
-   `custs1` obsahuje kolekci prvků řetězce, protože `cust.Name` je řetězec.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
-   `custs2` obsahuje kolekci `Customer` objekty, protože každý prvek `customers` je `Customer` objektu a celý prvek je vybrána v dotazu.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Však vhodné pojmenované typy nejsou vždy k dispozici. Můžete chtít vybrat jména zákazníků a adresy jediný účel, čísla ID zákazníka a umístění pro jiné a názvů zákazníka, adresy a historie objednávek pro třetí. Anonymní typy umožňují vybrat libovolnou kombinaci vlastnosti, v libovolném pořadí, bez první deklarace nového typu s názvem pro uchování výsledku. Místo toho kompilátor vytvoří pro každou kompilace vlastnosti anonymního typu. Následující dotaz vybere pouze zákazníka název a číslo ID z každého `Customer` objekt `customers`. Proto kompilátor vytvoří anonymního typu, který obsahuje pouze tyto dvě vlastnosti.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Názvy a datové typy vlastností v anonymním typu pocházejí ze argumenty, které mají `Select`, `cust.Name` a `cust.ID`. Vlastnosti v anonymním typu, který je vytvořen pomocí dotazu jsou vždy klíčové vlastnosti. Když `custs3` provádí v následujícím `For Each` smyčky, výsledek je kolekci instancí anonymního typu s dvě vlastnosti klíče `Name` a `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Prvky v kolekci reprezentována `custs3` jsou silného typu, a můžete použít technologii IntelliSense, procházení dostupných vlastností a jejich typy ověření.  
  
 Další informace najdete v tématu [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Rozhodování o tom, jestli se má použít anonymní typy  
 Před vytvořením objektu jako instance anonymní třídy, zvažte, jestli se jedná o nejlepší možnost. Pokud chcete vytvořit dočasný objekt tak, aby obsahovala souvisejících dat a nepotřebujete žádný další pole a metody, které mohou obsahovat na úplnou třídu, například anonymního typu je dobrým řešením. Anonymní typy jsou také pohodlný, pokud chcete, aby jiný výběr vlastnosti pro každou deklaraci, nebo pokud chcete změnit pořadí vlastnosti. Nicméně pokud váš projekt obsahuje několik objektů, které mají stejné vlastnosti v pevném pořadí, můžete je deklarovat snadněji pomocí pojmenovaného typu pomocí konstruktoru třídy. Například pomocí odpovídajícího konstruktoru, je jednodušší, chcete-li deklarovat několik instancí `Product` třídy, než je deklarovat několik instancí anonymního typu.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Další výhodou pojmenované typy je, že kompilátor může zachytit náhodnému chybným zadáním názvu vlastnosti. V předchozích příkladech `firstProd2`, `secondProd2`, a `thirdProd2` by měla být instance stejného anonymního typu. Ale pokud byste chtěli omylem deklarovat `thirdProd2` v jednom z následujících způsobů by jeho typu odlišného od `firstProd2` a `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Důležitější je existují omezení týkající se použití anonymních typů, které se nedá použít u instance pojmenovaných typů. `firstProd2`, `secondProd2`, a `thirdProd2` jsou instancemi stejného anonymního typu. Název sdílené anonymního typu však není k dispozici a nemůže být použit, kde se očekává název typu ve vašem kódu. Například anonymního typu nelze použít k definování podpis metody, chcete-li deklarovat jiné proměnné nebo pole nebo v jakékoli deklaraci typu. Anonymní typy v důsledku toho nejsou vhodné, když musíte sdílet informace pro všechny metody.  
  
## <a name="an-anonymous-type-definition"></a>Definici anonymního typu  
 V reakci na deklarace instanci anonymního typu kompilátor vytvoří novou definici třídy, která obsahuje zadané vlastnosti.  
  
 Pokud anonymní typ obsahuje alespoň jednu klíčovou vlastnost, přepíše definice tři členy zděděné z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, a <xref:System.Object.ToString%2A>. Kód vytvořený pro účely testování rovnosti a určení, že hodnota hash kódu bere v úvahu pouze klíčové vlastnosti. Pokud anonymní typ obsahuje žádné vlastnosti klíče, pouze <xref:System.Object.ToString%2A> je přepsána. Explicitně pojmenované vlastnosti anonymního typu nelze v konfliktu s těmito generované metody. To znamená, že nelze použít `.Equals`, `.GetHashCode`, nebo `.ToString` název vlastnosti.  
  
 Definice anonymního typu, které mají alespoň jednu klíčové vlastnosti také implementovat <xref:System.IEquatable%601?displayProperty=nameWithType> rozhraní, ve kterém `T` je typ anonymního typu.  
  
 Další informace o kód vytvořený pomocí kompilátoru a funkce přetížené metody, naleznete v tématu [definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
