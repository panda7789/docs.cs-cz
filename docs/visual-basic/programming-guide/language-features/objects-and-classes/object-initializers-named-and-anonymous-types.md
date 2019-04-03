---
title: 'Inicializátory objektů: Pojmenované a anonymní typy (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 6602a68555e37bf793ba41076ba8f484b4a0dbc3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821351"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicializátory objektů: Pojmenované a anonymní typy (Visual Basic)
Inicializátory objektů umožňují určit vlastnosti pro komplexní objekt s použitím jeden výraz. Může se použít pro vytvoření instancí typů pojmenované a anonymní typy.  
  
## <a name="declarations"></a>Deklarace  
 Deklarace pojmenované a anonymní typy instancí může vypadat téměř identické, ale jejich účinky nejsou stejné. Každá kategorie má schopnosti a omezení své vlastní. Následující příklad ukazuje pohodlný způsob, jak deklarovat a inicializovat třídu s názvem instance `Customer`, pomocí seznamu inicializátorů objektů. Všimněte si, že je zadán název třídy po klíčovém slovu `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Anonymní typ, který nemá žádný použitelný název. Proto instanci anonymního typu nelze zahrnout název třídy.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 Požadavky a výsledky dvě deklarace nejsou stejné. Pro `namedCust`, `Customer` třídu, která má `Name` vlastnost musí existovat a deklarace vytvoří instanci této třídy. Pro `anonymousCust`, kompilátor definuje novou třídu, která má jednu vlastnost, řetězec s názvem `Name`a vytvoří novou instanci této třídy.  
  
## <a name="named-types"></a>Pojmenované typy  
 Inicializátory objektů poskytují jednoduchý způsob, jak volat konstruktor typu a pak nastavte tyto hodnoty některé nebo všechny vlastnosti v jediném příkazu. Kompilátor vyvolá odpovídajícího konstruktoru pro příkaz: výchozí konstruktor, pokud jsou uvedeny žádné argumenty, nebo do parametrizovaného konstruktoru, pokud jeden nebo více argumentů se odesílají. Potom zadané vlastnosti jsou inicializovány v pořadí, ve kterém jsou uvedeny v seznamu inicializátorů.  
  
 Každý inicializace v seznamu inicializátorů se skládá z přiřazení počáteční hodnotu na člen třídy. Názvy a datové typy členů jsou určeny při je třída definovaná. V následujících příkladech `Customer` třídy musí existovat a musí obsahovat členy s názvem `Name` a `City` , který může přijmout hodnoty řetězce.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Stejného výsledku také můžete získat pomocí následujícího kódu:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Každá z těchto deklarace je ekvivalentní v následujícím příkladu, který vytvoří `Customer` objektu pomocí výchozího konstruktoru a poté určí počáteční hodnoty pro `Name` a `City` vlastnosti pomocí `With` příkaz.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Pokud `Customer` třída obsahuje parametrizované konstruktor, který vám umožní odesílat hodnotu pro `Name`, například můžete také deklarovat a inicializovat `Customer` objekt následujícími způsoby:  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Není potřeba inicializovat všechny vlastnosti, jako ukazuje následující kód.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Inicializační seznam však nemůže být prázdný. Neinicializovaných vlastností zachovat jejich výchozí hodnoty.  
  
### <a name="type-inference-with-named-types"></a>Odvození typu u pojmenovaných typů.  
 Můžete zkrátit kódu pro deklaraci `cust1` kombinací inicializátory objektů a odvození místního typu. To umožňuje vynechat, nechte `As` klauzule v deklaraci proměnné. Datový typ proměnné je odvozen z typu objektu, který je vytvořen pomocí přiřazení. V následujícím příkladu typ `cust6` je `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Poznámky o pojmenovaných typů  
  
-   Člen třídy nelze inicializovat více než jednou v seznamu inicializátorů objektů. Deklarace `cust7` způsobí chybu.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
-   Člen slouží k inicializaci sebe samu ani na jiné pole. Pokud člen je přístupná před inicializovaná, stejně jako v následující deklaraci pro `cust8`, bude použita výchozí hodnota. Mějte na paměti, že při zpracování deklarace, která používá inicializátor objektu první věc, ke které dochází, je, že je vyvolána odpovídajícího konstruktoru. Poté se inicializují jednotlivá pole v seznamu inicializátorů. V následujících příkladech, výchozí hodnota pro `Name` je přiřazen `cust8`, a inicializovaný hodnota přiřazená v `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     Následující příklad používá parametrizovaného konstruktoru z `cust3` a `cust4` deklarovat a inicializovat `cust10` a `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
-   Inicializátory objektů mohou být vnořené. V následujícím příkladu `AddressClass` je třída, která má dvě vlastnosti `City` a `State`a `Customer` třída má `Address` vlastnost, která je instance `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
-   Inicializační seznam nemůže být prázdný.  
  
-   Během inicializace instance nemůže být typu Object.  
  
-   Členy třídy, který je inicializován nemůže být sdílené členy, členy jen pro čtení, konstanty nebo volání metody.  
  
-   Členy třídy, který je inicializován nelze indexovat nebo kvalifikovaný. Následující příklady vyvolání chyby kompilátoru:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typy inicializátory objektů použít k vytvoření nových typů, které nejsou explicitně definovány a název instance. Místo toho kompilátor generuje typ podle vlastnosti, které určíte v seznamu inicializátorů objektů. Protože není zadaný název typu, to se označuje jako *anonymního typu*. Například následující deklaraci starší jeden z porovnat `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Syntakticky jediným rozdílem je, že není zadán žádný název po `New` datového typu. Ale co se stane, je značně odlišná. Kompilátor definuje nový anonymní typ, který má dvě vlastnosti `Name` a `City`a vytvoří její instanci se zadanými hodnotami. Určuje typy odvození typu `Name` a `City` v příkladu řetězce.  
  
> [!CAUTION]
>  Název anonymního typu je generovaný kompilátorem a se může lišit od kompilace do kompilace. Váš kód by neměl používat nebo Spolehněte se na název anonymního typu.  
  
 Protože název typu není k dispozici, nemůžete použít `As` klauzuli pro deklaraci `cust13`. Jeho typ musí být odvozený. Bez použití pozdní vazby, to omezuje použití anonymních typů pro lokální proměnné.  
  
 Anonymní typy umožňují podpory pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Další informace o použití anonymních typů v dotazech najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Poznámky o anonymních typech  
  
-   Všechny nebo většinu vlastností v deklaraci anonymního typu bude obvykle klíčové vlastnosti, které jsou označeny zadáním klíčového slova `Key` před název vlastnosti.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Další informace o vlastnosti klíče najdete v tématu [klíč](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Pojmenované typy, inicializační seznamy, jako je třeba pro definice anonymního typu musí deklarovat alespoň jednu vlastnost.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
-   Při deklaraci instanci anonymního typu, kompilátor vygeneruje odpovídající definici anonymního typu. Názvy a datové typy vlastností jsou převzaty z deklaraci instance a jsou zahrnuty v kompilátoru v definici. Vlastnosti nejsou s názvem a definovaný v předstihu, jako by se použily pro pojmenovaného typu. Jejich typy jsou odvozeny. Datové typy vlastností nelze zadat s použitím `As` klauzuli.  
  
-   Anonymní typy lze také vytvořit názvy a hodnoty jejich vlastností několika jinými způsoby. Vlastnosti anonymního typu může například trvat název a hodnotu proměnné, nebo název a hodnotu vlastnosti jiného objektu.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Další informace o možnostech pro definování vlastností anonymních typů najdete v tématu [jak: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Viz také:

- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Postupy: Odvození názvů a typů v deklaracích anonymního typu vlastností](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
