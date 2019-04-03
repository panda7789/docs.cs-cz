---
title: Obecné typy v jazyce Visual Basic (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- generic interfaces
- data type arguments [Visual Basic], defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures [Visual Basic], generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes [Visual Basic], Visual Basic
- parameters [Visual Basic], type
- type arguments
- interfaces [Visual Basic], generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generic structures [Visual Basic]
- generic classes [Visual Basic]
- type parameters
- data type arguments
- structures [Visual Basic], generic
- parameters [Visual Basic], data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
ms.openlocfilehash: 343c5c8e2625a1bd4279e0c97b7079482af0e8c6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831421"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Obecné typy v jazyce Visual Basic (Visual Basic)
A *obecného typu* je jediný prvek programování, které se přizpůsobí provádět stejné funkce pro širokou škálu datových typů. Při definování obecné třídy nebo proceduru není nutné definovat samostatné verze pro každý typ dat, pro které můžete chtít provést, které tuto funkci.  
  
 Analogie je šroubováku s vyměnitelné hlavy. Kontrola šroubovacím budete muset zapnout a vyberte správné hlavičky pro tento šroubovacím (s drážkou, překročí, označený hvězdičkou). Po vložení správný hlavní v popisovač šroubovák provádíte přesně stejnou funkci s šroubovák, a to zapnutím šroubek.  
  
 ![Diagram šroubováku s jinou hlavy.](./media/generic-types/generic-screwdriver-set.gif)  
  
 Při definování obecného typu parametrizovat u jednoho nebo více datových typů. Díky tomu pomocí kódu pro přizpůsobení své požadavky na datové typy. Váš kód může deklarovat několik různých programovací prvky z obecného prvku, každý z nich na jinou sadu datových typů. Ale všechny deklarované elementy provádět stejné logiky, bez ohledu na to, jaké typy dat, které využívají.  
  
 Například můžete chtít vytvořit a používat fronty třídu, která funguje na určitý datový typ. například `String`. Je možné deklarovat třídu z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Teď můžete použít `stringQ` pracovat pouze s `String` hodnoty. Protože `stringQ` je specifické pro `String` místo se zobecnit pro `Object` hodnoty, není nutné pozdní vazby nebo typ převodu. Tím ušetříte čas spuštění a snižuje chyby za běhu.  
  
 Další informace o použití obecného typu, najdete v části [jak: Použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Příklad obecné třídy  
 Následující příklad ukazuje definici kostru obecné třídy.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 V předchozím kostru `t` je *parametr typu*, to znamená, zástupný symbol pro datový typ, který zadáte při deklaraci třídy. Kdekoli v kódu, je možné deklarovat různé verze `classHolder` zadáním různých datových typů pro `t`. Následující příklad ukazuje dva takové deklarace.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 Předchozí příkaz deklarují *vytvořený třídy*, ve kterém nahradí určitý typ parametru typu. Toto nahrazení se šíří v rámci kódu v rámci vytvořeného třídy. Následující příklad ukazuje, co `processNewItem` postup vypadá podobně jako v `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Podrobnější příklad naleznete v tématu [jak: Definujte třídu, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Oprávněné programovací elementy  
 Můžete definovat a použití obecné třídy, struktury, rozhraní, postupy a delegáti. Všimněte si, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definuje několik obecných tříd, struktur a rozhraní, která představuje běžně používané obecné elementy. <xref:System.Collections.Generic?displayProperty=nameWithType> Obor názvů poskytuje slovníky, seznamů, front a zásobníků. Než začnete definovat vlastní obecného prvku, zjistěte, zda je již k dispozici v <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Postupy nejsou typy, ale můžete definovat a používat obecné procedury. Zobrazit [obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Výhody obecných typů  
 Obecný typ slouží jako základ pro deklarování několik různých programovací prvky, z nichž každý pracuje na konkrétní data typu. Alternativy k obecného typu jsou:  
  
1.  Jeden typ provozující `Object` datového typu.  
  
2.  Sada *specifické pro typ.* verze typu, každá verze jednotlivě programového a provozování na jeden konkrétní datový typ jako `String`, `Integer`, nebo uživatelem definovaný typ, jako `customer`.  
  
 Obecný typ má následující výhody oproti tyto alternativy:  
  
-   **Bezpečnost typů.** Obecné typy vynucovat kontrola typu v době kompilace. Na základě typů `Object` přijmout libovolný typ dat a je nutné napsat kód ke kontrole, jestli vstupní datový typ je přijatelné. Pomocí obecných typů kompilátor může zachytit neshody typů před časem spuštění.  
  
-   **Výkon.** Obecné typy nemusíte *pole* a *rozbalení* dat, protože každé z nich se specializuje na jednoho datového typu. Operace na základě `Object` musí pole vstupních datových typů a převést tak, aby `Object` a rozbalení určeného pro výstupní data. Zabalení a rozbalení snížit výkon.  
  
     Na základě typů `Object` jsou také s pozdní vazbou, což znamená, že přístup k jejich členům vyžaduje zvláštní kód za běhu. To také snižuje výkon.  
  
-   **Sloučení kódu.** Kód v obecném typu musí být definován pouze jednou. Sada specifické pro typ. verze tohoto typu musí replikovat stejný kód v jednotlivých verzích s jediným rozdílem je typ data specifická pro danou verzi. Pomocí obecných typů se všechny verze specifické pro typ. generují z původní obecného typu.  
  
-   **Opakované použití kódu.** Pokud není obecný, můžete použít kód, který není závislý na konkrétní datový typ opakovaně s různými datovými typy. Můžete ho využít často i s datovým typem, který jste není předpovědět původně.  
  
-   **Podpora integrované vývojové prostředí.** Pokud používáte konstruovaný typ deklarovaný z obecného typu, integrované vývojové prostředí (IDE) vám může poskytnout další podporu při vývoji kódu. Technologie IntelliSense můžete můžete například zobrazit možnosti specifické pro typ. pro argument do konstruktoru nebo metody.  
  
-   **Obecné algoritmy.** Abstraktní algoritmy, které jsou nezávislé na typ jsou vhodnými kandidáty pro obecné typy. Například obecný postup, který seřadí položky pomocí <xref:System.IComparable> rozhraní je možné s datovým typem, který implementuje <xref:System.IComparable>.  
  
## <a name="constraints"></a>Omezení  
 I když kód v definici obecného typu musí být typu jako nezávislé co nejvíc, můžete potřebovat vyžadovat schopnost žádný datový typ zadaný pro obecný typ. Například pokud chcete porovnat dvě položky pro účely řazení nebo řazení, jejich datový typ musí implementovat <xref:System.IComparable> rozhraní. Tento požadavek můžete vynutit tak, že přidáte *omezení* na parametr typu.  
  
### <a name="example-of-a-constraint"></a>Příklad omezení  
 Následující příklad ukazuje definici kostru třídy s omezením, který vyžaduje argument typu pro implementaci <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Pokud následující kód se pokusí vytvořit třídu z `itemManager` zadáním typu, který neimplementuje <xref:System.IComparable>, kompilátor signály chybu.  
  
### <a name="types-of-constraints"></a>Typy omezení  
 Vaše omezení můžete zadat v libovolnou kombinaci následující požadavky:  
  
-   Argument typu musí implementovat jedno nebo více rozhraní  
  
-   Argument typu musí být typu nebo dědí nejvýše jednu třídu  
  
-   Argument typu musí vystavit přístupné pro kód, který vytvoří objekty z něj konstruktor bez parametrů  
  
-   Argument typu musí být *odkazovat na typ*, nebo musí být *typ hodnoty*  
  
 Pokud potřebujete uložit více než jeden požadavek, můžete použít oddělených čárkou *seznam omezení* uvnitř složených závorek (`{ }`). Tak, aby vyžadovala přístupný konstruktor, můžete zahrnout [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo v seznamu. Tak, aby vyžadovala odkazový typ, můžete zahrnout `Class` – klíčové slovo; tak, aby vyžadovala typem hodnoty zahrnete `Structure` – klíčové slovo.  
  
 Další informace o omezení, najdete v části [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Příklad více omezení  
 Následující příklad ukazuje definici kostru obecné třídy se seznamem omezení u parametru typu. V kódu, který vytvoří instanci této třídy, argument typu musí implementovat obě <xref:System.IComparable> a <xref:System.IDisposable> rozhraní být typ odkazu, tak a zpřístupnit dostupný konstruktor bez parametrů.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Důležité termíny  
 Obecné typy představují a používají následující termíny:  
  
-   *Obecný typ*. Definice třídy, struktury, rozhraní, procedury nebo pro kterou je zadat alespoň jeden datový typ při jeho deklaraci delegáta.  
  
-   *Parametr typu*. V definici obecného typu zástupný symbol pro datový typ je zadat při deklaraci typu.  
  
-   *Argument typu*. Konkrétní datový typ, který nahrazuje parametr typu, když deklarujete konstruovaný typ z obecného typu.  
  
-   *Omezení*. Podmínka pro parametr typu, který omezí typ argumentu, kterou zadáte pro něj. Omezení může vyžadovat, že argument typu musí implementovat určité rozhraní, být nebo dědit z dané třídy, mít dostupný konstruktor bez parametrů nebo být typu odkaz nebo typ hodnoty. Tato omezení můžete kombinovat, ale můžete zadat maximálně jednu třídu.  
  
-   *Konstruovaný typ*. Třídy, struktury, rozhraní, procedura nebo delegát deklarován zadáním argumentů typu pro svoje parametry typu z obecného typu.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [z](../../../../visual-basic/language-reference/statements/of-clause.md)
- [jako](../../../../visual-basic/language-reference/statements/as-clause.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Kovariance a kontravariance](../../concepts/covariance-contravariance/index.md)
- [Iterátory](../../../../visual-basic/programming-guide/concepts/iterators.md)
