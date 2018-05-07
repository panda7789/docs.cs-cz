---
title: 'Inicializátory objektů: pojmenované a anonymní typy (Visual Basic)'
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
ms.openlocfilehash: 612b1dcea0f776dfd4580803e76f2785e7d28da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicializátory objektů: pojmenované a anonymní typy (Visual Basic)
Inicializátory objektů umožňují určit vlastnosti pro komplexní objekt pomocí jeden výraz. Může se použít k vytvoření instance pojmenované typy a anonymní typy.  
  
## <a name="declarations"></a>Deklarace  
 Deklarace instancí pojmenované a anonymní typy může vypadat téměř shodné, ale jejich důsledky nejsou stejné. Každá kategorie obsahuje dalo a vlastní omezení. Následující příklad ukazuje pohodlný způsob, jak deklarace a Inicializace instance třídy s názvem `Customer`, použít seznam inicializátoru objektu. Všimněte si, zda je zadán název třídy po klíčové slovo `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 Anonymní typ nemá žádný použitelný název. Proto vytváření instancí anonymního typu nesmí obsahovat název třídy.  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 Požadavky a výsledky dvě deklarace nejsou stejné. Pro `namedCust`, `Customer` třídu, která má `Name` vlastnost již musí existovat a vytvoří deklaraci instance této třídy. Pro `anonymousCust`, kompilátor definuje novou třídu, která má jednu vlastnost, řetězec s názvem `Name`a vytvoří novou instanci třídy.  
  
## <a name="named-types"></a>Pojmenované typy  
 Inicializátory objektů poskytují jednoduchý způsob, jak volat konstruktor typu a potom nastavte hodnoty některé nebo všechny vlastnosti v jediném příkazu. Kompilátor vyvolá odpovídající konstruktor pro příkaz: výchozí konstruktor, pokud jsou uvedené žádné argumenty nebo parametrizované konstruktoru, pokud jeden nebo více argumentů se odesílají. Potom se v pořadí, ve kterém jsou uvedeny v seznamu inicializátoru inicializují zadané vlastnosti.  
  
 Každý inicializace v seznamu inicializátoru se skládá z přiřazení počáteční hodnota pro člena třídy. Názvy a datové typy členů jsou určeny, když je třída definovaná. V následujících příkladech `Customer` třída musí existovat a musí mít členy s názvem `Name` a `City` který může přijmout hodnoty řetězce.  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 Alternativně můžete získat stejný výsledek pomocí následujícího kódu:  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 Každý z těchto deklarace je ekvivalentní v následujícím příkladu vytvoří `Customer` objektu pomocí výchozí konstruktor a pak specifikuje počáteční hodnoty `Name` a `City` vlastnosti pomocí `With` příkaz.  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 Pokud `Customer` třída obsahuje parametrizované konstruktor, který vám umožní odesílat hodnotu pro `Name`, například můžete také deklarovat a inicializaci `Customer` objekt následujícími způsoby:  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 Nemáte k chybě při inicializaci všechny vlastnosti, jak ukazuje následující kód.  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 Inicializace seznamu však nemůže být prázdný. Neinicializovaný vlastnosti zachovat jejich výchozí hodnoty.  
  
### <a name="type-inference-with-named-types"></a>Odvození typu s pojmenované typy  
 Můžete zkrátit kód pro deklaraci `cust1` kombinací inicializátory objektu a odvození místního typu. Díky tomu můžete vynechat `As` klauzuli v deklarace proměnné. Datový typ proměnné je odvozený z typu objektu, který je vytvořen pomocí přiřazení. V následujícím příkladu, typ `cust6` je `Customer`.  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>Poznámky o pojmenované typy  
  
-   Člena třídy nelze inicializovat více než jednou v seznamu inicializátoru objektu. Prohlášení o `cust7` dojde k chybě.  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   Člen slouží k inicializaci sám sebe nebo jiné pole. Pokud člen přistupuje předtím, než ji bylo inicializováno, stejně jako deklarace `cust8`, bude použita výchozí hodnota. Mějte na paměti, že při zpracování deklaraci, která používá inicializátoru objektu je první věcí, kterou se stane, je, že je vhodný konstruktor vyvolán. Poté jsou jednotlivá pole v seznamu inicializátoru inicializovány. V následujících příkladech, výchozí hodnota pro `Name` je přiřazen pro `cust8`, a inicializovaného hodnota přiřazená v `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     Následující příklad používá parametrizované konstruktoru z `cust3` a `cust4` deklarace a inicializace `cust10` a `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   Inicializátory objektů mohou být použity. V následujícím příkladu `AddressClass` je třída, která má dvě vlastnosti `City` a `State`a `Customer` třída má `Address` vlastnost, která je instance `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   Inicializace seznam nesmí být prázdný.  
  
-   Během inicializace instance nesmí být typu objektu.  
  
-   Členy třídy inicializován nemůže být sdílení členové, členové jen pro čtení, konstanty nebo volání metod.  
  
-   Členy třídy během inicializace nelze indexovat nebo kvalifikovaný. Následující příklady vyvolání chyby kompilátoru:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typy inicializátory objektů použít k vytvoření instance nové typy, které nejsou explicitně definovány a název. Místo toho kompilátor generuje typu podle vlastnosti, které určíte v seznamu inicializátoru objektu. Protože není určen název typu, se odkazuje jako *anonymního typu*. Například porovnat následující prohlášení na dřívější jeden z `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 Syntakticky jediným rozdílem je, že není zadán žádný název po `New` pro datový typ. Co se stane, je však výrazně lišit. Kompilátor definuje nový anonymní typ, který má dvě vlastnosti `Name` a `City`a vytvoří její instanci se zadanými hodnotami. Odvození typu Určuje typy `Name` a `City` v příkladu jako řetězce.  
  
> [!CAUTION]
>  Název typu anonymní je generován kompilátor a se může lišit od kompilace kompilace. Váš kód by neměl používat nebo spoléhají na název anonymního typu.  
  
 Protože název typu není k dispozici, nemůžete použít `As` klauzule deklarovat `cust13`. Typ musí být odvozený. Bez použití pozdní vazba, toto omezení použití anonymní typy na místní proměnné.  
  
 Anonymní typy poskytují důležité podporu pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy. Další informace o použití anonymní typy v dotazech najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Poznámky o anonymních typech  
  
-   Obvykle se klíčové vlastnosti, které jsou označeny zadáním klíčové slovo bude všechny nebo většinu vlastností v deklaraci anonymního typu `Key` před název vlastnosti.  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     Další informace o vlastnosti klíče najdete v tématu [klíč](../../../../visual-basic/language-reference/modifiers/key.md).  
  
-   Jako s názvem typy, inicializační seznamy pro anonymní typ definice musí deklarovat alespoň jednu vlastnost.  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   Pokud je deklarovaná instanci anonymního typu, kompilátor vygeneruje odpovídající definice autonomního typu. Názvy a datové typy vlastností jsou převzaty z deklaraci instance a jsou zahrnuty kompilátorem v definici. Vlastnosti nejsou s názvem a definovat předem, jako by byly pro pojmenovaného typu. Jejich typy jsou odvodit. Datové typy vlastností nelze zadat pomocí `As` klauzule.  
  
-   Anonymní typy můžete také vytvořit názvy a hodnoty jejich vlastnosti několik jinými způsoby. Ve vlastnosti anonymního typu může například trvat název a hodnotu proměnné, nebo název a hodnotu vlastnosti jiného objektu.  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     Další informace o možnostech pro definování vlastností v anonymní typy najdete v tématu [postupy: odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Viz také  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)  
 [Postupy: Deklarace objektu pomocí inicializátoru objektu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
