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
ms.openlocfilehash: e1f461cc98fb104f78a6c83a207cff7f4eda9227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046451"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Inicializátory objektů: Pojmenované a anonymní typy (Visual Basic)
Inicializátory objektů umožňují určit vlastnosti složitého objektu pomocí jediného výrazu. Lze je použít k vytvoření instancí pojmenovaných typů a anonymních typů.  
  
## <a name="declarations"></a>Deklarace  
 Deklarace instancí pojmenovaných a anonymních typů mohou vypadat téměř stejně, ale jejich účinky nejsou stejné. Každá kategorie má možnosti a omezení vlastního typu. Následující příklad ukazuje pohodlný způsob, jak deklarovat a inicializovat instanci pojmenované třídy, `Customer`pomocí seznamu inicializátorů objektů. Všimněte si, že název třídy je zadán za klíčovým slovem `New`.  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Anonymní typ nemá žádný použitelný název. Proto vytváření instancí anonymního typu nemůže obsahovat název třídy.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 Požadavky a výsledky těchto dvou deklarací nejsou stejné. Třída, která má`Name` vlastnost, musí již existovat a deklarace vytvoří instanci této třídy. `namedCust` `Customer` Pro `anonymousCust`definuje kompilátor novou třídu, která má jednu vlastnost, řetězec nazvaný `Name`a vytvoří novou instanci této třídy.  
  
## <a name="named-types"></a>Pojmenované typy  
 Inicializátory objektů poskytují jednoduchý způsob volání konstruktoru typu a poté nastavení hodnot některých nebo všech vlastností v jednom příkazu. Kompilátor vyvolá příslušný konstruktor pro příkaz: konstruktor bez parametrů, pokud nejsou zadány žádné argumenty, nebo parametrizovaný konstruktor při odeslání jednoho nebo více argumentů. Poté jsou zadané vlastnosti inicializovány v pořadí, ve kterém jsou uvedeny v seznamu inicializátorů.  
  
 Každá inicializace v seznamu inicializátorů se skládá z přiřazení počáteční hodnoty ke členu třídy. Názvy a datové typy členů jsou určeny při definování třídy. V následujících příkladech `Customer` musí třída existovat a musí mít členy s názvem `Name` a `City` , které mohou přijímat řetězcové hodnoty.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Alternativně můžete získat stejný výsledek pomocí následujícího kódu:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Každá z těchto deklarací je `Customer` ekvivalentní následujícímu příkladu, který vytvoří objekt pomocí konstruktoru bez parametrů a pak určí počáteční hodnoty `Name` vlastností `With` a `City` pomocí vydá.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Pokud třída obsahuje parametrizovaný konstruktor, který umožňuje odeslat `Name`hodnotu například, můžete deklarovat a inicializovat `Customer` objekt následujícími způsoby: `Customer`  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Nemusíte inicializovat všechny vlastnosti, jak ukazuje následující kód.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Inicializační seznam ale nemůže být prázdný. Neinicializované vlastnosti uchovávají jejich výchozí hodnoty.  
  
### <a name="type-inference-with-named-types"></a>Odvození typu s pojmenovanými typy  
 Můžete zkrátit kód pro deklaraci `cust1` pomocí kombinování inicializátorů objektů a místního odvození typu. To umožňuje vynechat `As` klauzuli v deklaraci proměnné. Datový typ proměnné je odvozen z typu objektu, který je vytvořen přiřazením. V následujícím příkladu `cust6` je `Customer`typ typu.  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Poznámky k pojmenovaným typům  
  
- Člen třídy nelze v seznamu inicializátoru objektu inicializovat více než jednou. Deklarace `cust7` způsobuje chybu.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- Člen lze použít k inicializaci samotného nebo jiného pole. Pokud je před inicializací členem k dispozici člen, jako v následující deklaraci pro `cust8`, bude použita výchozí hodnota. Pamatujte, že pokud je zpracována deklarace, která používá inicializátor objektu, první věc, ke které dojde, je vyvolán příslušný konstruktor. Poté jsou inicializována jednotlivá pole v seznamu inicializátorů. V následujících příkladech `Name` je `cust8`přiřazena výchozí hodnota pro a inicializovaná hodnota je přiřazena v `cust9`.  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     Následující příklad `cust3` používá parametrizovaný konstruktor z a `cust4` k deklaraci a inicializaci `cust10` a `cust11`.  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Inicializátory objektů můžou být vnořené. V `AddressClass` následujícím příkladu je třída, která má dvě vlastnosti, `City` a `State`a `Customer` třída má `Address` vlastnost, která je instancí `AddressClass`.  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- Seznam inicializace nemůže být prázdný.  
  
- Inicializovaná instance nemůže být typu Object.  
  
- Členy třídy, které jsou inicializovány, nemohou být sdíleny členy, členy jen pro čtení, konstanty nebo volání metod.  
  
- Inicializace členů třídy nemůže být indexována ani kvalifikována. Následující příklady vyvolávají chyby kompilátoru:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typy používají Inicializátory objektů k vytváření instancí nových typů, které nemusíte explicitně definovat a pojmenovat. Místo toho kompilátor vygeneruje typ podle vlastností, které určíte v seznamu inicializátorů objektů. Vzhledem k tomu, že název typu není zadán, je označován jako *anonymní typ*. Porovnejte například následující deklaraci na předchozí `cust6`.  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 Jediným rozdílem syntakticky je, že `New` pro datový typ není zadaný žádný název. K čemu ale dojde poměrně jinak. Kompilátor definuje nový anonymní typ, který má dvě vlastnosti, `Name` a `City`a vytvoří jeho instanci se zadanými hodnotami. Odvození typu Určuje typy `Name` a `City` v příkladu, které mají být řetězce.  
  
> [!CAUTION]
> Název anonymního typu je generován kompilátorem a může se lišit od kompilace po kompilaci. Váš kód by neměl používat nebo spoléhat na název anonymního typu.  
  
 Vzhledem k tomu, že název typu není k dispozici, nelze použít `As` klauzuli k deklaraci. `cust13` Jeho typ musí být odvozený. Bez použití pozdní vazby omezuje použití anonymních typů na lokální proměnné.  
  
 Anonymní typy poskytují kritickou podporu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pro dotazy. Další informace o použití anonymních typů v dotazech naleznete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) a [Úvod do LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Poznámky k anonymním typům  
  
- Obvykle všechny nebo většina vlastností v deklaraci anonymního typu budou mít klíčové vlastnosti, které jsou označeny zadáním klíčového slova `Key` před názvem vlastnosti.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Další informace o vlastnostech klíče najdete v tématu [Key](../../../../visual-basic/language-reference/modifiers/key.md).  
  
- Podobně jako pojmenované typy, inicializační seznamy pro definice anonymního typu musí deklarovat alespoň jednu vlastnost.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- Je-li deklarována instance anonymního typu, kompilátor vygeneruje vyhovující definici anonymního typu. Názvy a datové typy vlastností jsou odebírány z deklarace instance a jsou součástí kompilátoru v definici. Vlastnosti nejsou pojmenované a jsou definovány předem, protože by byly pro pojmenovaný typ. Jejich typy jsou odvozeny. Datové typy vlastností nelze zadat pomocí `As` klauzule.  
  
- Anonymní typy mohou také vytvořit názvy a hodnoty jejich vlastností několika různými způsoby. Například vlastnost anonymního typu může převzít název i hodnotu proměnné nebo název a hodnotu vlastnosti jiného objektu.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Další informace o možnostech definování vlastností v anonymních typech naleznete v tématu [How to: Odvodit názvy vlastností a typy v deklaracích](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)anonymního typu.  
  
## <a name="see-also"></a>Viz také:

- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektu](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
