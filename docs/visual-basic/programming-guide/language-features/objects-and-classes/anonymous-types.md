---
title: Anonymní typy
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 064c43274069be3951f816eaafafac0bbece7651
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347162"
---
# <a name="anonymous-types-visual-basic"></a>Anonymní typy (Visual Basic)
Visual Basic podporuje anonymní typy, které umožňují vytvářet objekty bez psaní definice třídy pro datový typ. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název, dědí přímo z <xref:System.Object>a obsahuje vlastnosti, které zadáte v deklaraci objektu. Vzhledem k tomu, že název datového typu není zadán, je označován jako *anonymní typ*.  
  
 Následující příklad deklaruje a vytvoří proměnnou `product` jako instanci anonymního typu, který má dvě vlastnosti, `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 *Výraz dotazu* používá anonymní typy pro kombinování sloupců dat vybraných dotazem. Typ výsledku nelze definovat předem, protože nemůžete předpovědět sloupce, které může konkrétní dotaz vybrat. Anonymní typy umožňují napsat dotaz, který vybere libovolný počet sloupců, v libovolném pořadí. Kompilátor vytvoří datový typ, který odpovídá zadaným vlastnostem a určenému pořadí.  
  
 V následujících příkladech je `products` seznam objektů produktu, z nichž každá má mnoho vlastností. Proměnná `namePriceQuery` obsahuje definici dotazu, který při spuštění vrátí kolekci instancí anonymního typu, které mají dvě vlastnosti, `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 Proměnná `nameQuantityQuery` obsahuje definici dotazu, který při spuštění vrátí kolekci instancí anonymního typu, které mají dvě vlastnosti, `Name` a `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Další informace o kódu vytvořeném kompilátorem pro anonymní typ naleznete v tématu [definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
> Název anonymního typu je generovaný kompilátorem a může se lišit od kompilace po kompilaci. Váš kód by neměl používat nebo spoléhat na název anonymního typu, protože název se může změnit, když je projekt znovu zkompilován.  
  
## <a name="declaring-an-anonymous-type"></a>Deklarace anonymního typu  
 Deklarace instance anonymního typu používá seznam inicializátorů k určení vlastností typu. Můžete určit vlastnosti pouze při deklaraci anonymního typu, nikoli jiných prvků třídy, jako jsou metody nebo události. V následujícím příkladu je `product1` instance anonymního typu, který má dvě vlastnosti: `Name` a `Price`.  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Pokud určíte vlastnosti jako klíčové vlastnosti, můžete je použít k porovnání dvou instancí anonymního typu pro rovnost. Hodnoty vlastností klíče však nelze změnit. Další informace najdete v části vlastnosti klíče dále v tomto tématu.  
  
 Všimněte si, že deklarace instance anonymního typu je jako deklarace instance pojmenovaného typu pomocí inicializátoru objektu:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Další informace o dalších způsobech určení vlastností anonymního typu naleznete v tématu [How to: odvozování názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti se liší od neklíčových vlastností několika základními způsoby:  
  
- Porovnávají se pouze hodnoty vlastností klíče, aby bylo možné určit, zda jsou dvě instance stejné.  
  
- Hodnoty vlastností klíče jsou jen pro čtení a nelze je změnit.  
  
- V algoritmu hash generovaném kompilátorem pro anonymní typ jsou zahrnuty pouze hodnoty vlastností Key.  
  
### <a name="equality"></a>Rovnost  
 Instance anonymních typů mohou být stejné pouze v případě, že jsou instancemi stejného anonymního typu. Kompilátor zpracovává dvě instance jako instance stejného typu, pokud splňují následující podmínky:  
  
- Jsou deklarovány ve stejném sestavení.  
  
- Jejich vlastnosti mají stejné názvy, stejné odvozené typy a jsou deklarovány ve stejném pořadí. Porovnávání názvů nerozlišuje velká a malá písmena.  
  
- Stejné vlastnosti v každé z nich jsou označeny jako klíčové vlastnosti.  
  
- Nejméně jedna vlastnost v každé deklaraci je klíčová vlastnost.  
  
 Instance anonymních typů, které nemají žádné klíčové vlastnosti, se rovná pouze sobě.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Dvě instance stejného anonymního typu jsou stejné, pokud jsou hodnoty jejich klíčových vlastností stejné. Následující příklady ilustrují způsob testování rovnosti.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Hodnoty jen pro čtení  
 Hodnoty vlastností klíče nelze změnit. Například v `prod8` v předchozím příkladu jsou pole `Name` a `Price` `read-only`, ale `OnHand` lze změnit.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Anonymní typy z výrazů dotazů  
 Výrazy dotazu nevyžadují vždy vytváření anonymních typů. Pokud je to možné, používají existující typ k uchování dat sloupce. K tomu dojde, když dotaz vrátí buď celé záznamy ze zdroje dat, nebo pouze jedno pole z každého záznamu. V následujících příkladech kódu `customers` je kolekce objektů `Customer` třídy. Třída má mnoho vlastností a můžete do výsledku dotazu zahrnout jednu nebo více z nich, a to v libovolném pořadí. V prvních dvou příkladech nejsou vyžadovány anonymní typy, protože dotazy vyberou prvky pojmenovaných typů:  
  
- `custs1` obsahuje kolekci řetězců, protože `cust.Name` je řetězec.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2` obsahuje kolekci objektů `Customer`, protože každý prvek `customers` je objekt `Customer` a celý element je vybrán dotazem.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Odpovídající pojmenované typy však nejsou vždy k dispozici. Můžete chtít vybrat jména a adresy zákazníků pro jeden účel, čísla ID zákazníka a umístění pro jiné, jména zákazníků, adresy a historie objednávek pro třetí. Anonymní typy umožňují vybrat libovolnou kombinaci vlastností, v libovolném pořadí bez první deklarace nového pojmenovaného typu pro uložení výsledku. Místo toho kompilátor vytvoří anonymní typ pro každou kompilaci vlastností. Následující dotaz vybere pouze jméno zákazníka a číslo ID z každého objektu `Customer` v `customers`. Proto kompilátor vytvoří anonymní typ, který obsahuje pouze tyto dvě vlastnosti.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Názvy i datové typy vlastností anonymního typu jsou odebírány z argumentů `Select`, `cust.Name` a `cust.ID`. Vlastnosti v anonymním typu, který je vytvořen dotazem, jsou vždy vlastnosti klíče. Když se `custs3` spustí v následující `For Each` smyčce, výsledkem je kolekce instancí anonymního typu se dvěma vlastnostmi klíče, `Name` a `ID`.  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Prvky v kolekci reprezentované `custs3` jsou silného typu a můžete použít technologii IntelliSense k procházení dostupných vlastností a k ověření jejich typů.  
  
 Další informace najdete v tématu [Úvod do LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Rozhodnutí, jestli se mají používat anonymní typy  
 Před vytvořením objektu jako instance anonymní třídy zvažte, zda se jedná o nejlepší možnost. Například pokud chcete vytvořit dočasný objekt, který bude obsahovat související data, a nepotřebujete další pole a metody, které může kompletní třída obsahovat, anonymní typ je dobrým řešením. Anonymní typy jsou také vhodné, pokud chcete pro každou deklaraci vybrat jinou vlastnost, nebo pokud chcete změnit pořadí vlastností. Nicméně pokud váš projekt obsahuje několik objektů, které mají stejné vlastnosti v určitém pořadí, můžete je deklarovat snadněji pomocí pojmenovaného typu s konstruktorem třídy. Například s vhodným konstruktorem je snazší deklarovat několik instancí `Product` třídy, než je deklarováno několika instancí anonymního typu.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Další výhodou pojmenovaných typů je, že kompilátor může zachytit náhodné chybné zadání názvu vlastnosti. V předchozích příkladech jsou `firstProd2`, `secondProd2`a `thirdProd2` určeny jako instance stejného anonymního typu. Pokud jste však nechtěně deklarovali `thirdProd2` jedním z následujících způsobů, jeho typ by se lišil od `firstProd2` a `secondProd2`.  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Důležitější je ale omezení používání anonymních typů, které se nevztahují na instance pojmenovaných typů. `firstProd2`, `secondProd2`a `thirdProd2` jsou instance stejného anonymního typu. Název sdíleného anonymního typu ale není k dispozici a nemůže se objevit tam, kde se v kódu očekává název typu. Například anonymní typ nelze použít k definování signatury metody, k deklarování jiné proměnné nebo pole nebo v jakékoli deklaraci typu. V důsledku toho nejsou anonymní typy vhodné, pokud je nutné sdílet informace napříč metodami.  
  
## <a name="an-anonymous-type-definition"></a>Definice anonymního typu  
 V reakci na deklaraci instance anonymního typu kompilátor vytvoří novou definici třídy obsahující zadané vlastnosti.  
  
 Pokud anonymní typ obsahuje alespoň jednu vlastnost klíče, přepíše definice tři členy zděděné z <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>a <xref:System.Object.ToString%2A>. Kód vytvořený pro testování rovnosti a určení hodnoty hash kódu považuje jenom vlastnosti klíče. Pokud anonymní typ neobsahuje žádné vlastnosti klíče, bude přepsána pouze <xref:System.Object.ToString%2A>. Explicitní pojmenované vlastnosti anonymního typu nejsou v konfliktu s těmito generovanými metodami. To znamená, že nemůžete použít `.Equals`, `.GetHashCode`nebo `.ToString` k pojmenování vlastnosti.  
  
 Definice anonymního typu, které mají alespoň jednu vlastnost klíče, implementují rozhraní <xref:System.IEquatable%601?displayProperty=nameWithType>, kde `T` je typ anonymního typu.  
  
 Další informace o kódu vytvořeném kompilátorem a funkcích přepsaných metod naleznete v tématu [definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Definice anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
