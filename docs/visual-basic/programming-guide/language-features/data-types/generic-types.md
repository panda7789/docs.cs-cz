---
title: Obecné typy
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
ms.openlocfilehash: 3dcd7756b10fab8f66f4d5c10acedd8f600eb2e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350122"
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Obecné typy v jazyce Visual Basic (Visual Basic)
*Obecný typ* je jediný programovací prvek, který se přizpůsobí tak, aby prováděl stejnou funkčnost pro celou řadu datových typů. Při definování obecné třídy nebo procedury není nutné definovat samostatnou verzi pro každý datový typ, pro který byste mohli chtít tuto funkci provést.  
  
 Analogie je Screwdriver sada s vyměnitelnými hlavami. Kontrolujete šroub, který potřebujete, abyste mohli zapnout a vybrat správnou hlavu pro daný šroub (s drážkou, překříženým označených hvězdičkou). Po vložení správného záhlaví v popisovači Screwdriver provedete přesnou stejnou funkci s Screwdriver, a to tak, že zapnete šroub.  
  
 ![Diagram Screwdriver sady s různými hlavami](./media/generic-types/generic-screwdriver-set.gif)  
  
 Definujete-li obecný typ, můžete ho parametrizovat pomocí jednoho nebo více datových typů. To umožňuje, aby kód používal k přizpůsobení datových typů požadavkům. Váš kód může deklarovat několik různých programovacích prvků z obecného prvku, každý z nich působí na jinou sadu datových typů. Ale deklarované prvky všechny provádějí stejnou logiku bez ohledu na to, jaké typy dat používají.  
  
 Například můžete chtít vytvořit a použít třídu fronty, která pracuje na konkrétním datovém typu, například `String`. Takovou třídu lze deklarovat z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrDataTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#1)]  
  
 Nyní můžete použít `stringQ` pro práci výhradně s `String` hodnotami. Vzhledem k tomu, že `stringQ` je specifické pro `String` namísto zobecnění pro `Object` hodnoty, nemáte pozdní vazbu nebo převod typu. Tím se ušetří čas spuštění a zkracuje se běhové chyby.  
  
 Další informace o použití obecného typu naleznete v tématu [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Příklad obecné třídy  
 Následující příklad ukazuje kostru definice obecné třídy.  
  
 [!code-vb[VbVbalrDataTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#2)]  
  
 V předchozí kostra je `t` *parametr typu*, tedy zástupný symbol pro datový typ, který zadáte při deklaraci třídy. Jinde v kódu můžete deklarovat různé verze `classHolder` poskytnutím různých datových typů pro `t`. Následující příklad ukazuje dvě takové deklarace.  
  
 [!code-vb[VbVbalrDataTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#3)]  
  
 Předchozí příkazy deklaruje *konstruované třídy*, ve kterých konkrétní typ nahradí parametr typu. Tato náhrada je šířena v celém kódu v rámci konstruované třídy. Následující příklad ukazuje, jak `processNewItem` procedura vypadá jako v `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#4)]  
  
 Úplnější příklad naleznete v tématu [How to: define a Class, která může poskytovat identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Oprávněné programovací prvky  
 Můžete definovat a používat obecné třídy, struktury, rozhraní, procedury a delegáty. Všimněte si, že .NET Framework definuje několik obecných tříd, struktur a rozhraní, které reprezentují běžně používané obecné prvky. Obor názvů <xref:System.Collections.Generic?displayProperty=nameWithType> poskytuje slovníky, seznamy, fronty a zásobníky. Před definováním vlastního obecného prvku zkontrolujte, zda je již k dispozici v <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Procedury nejsou typy, ale můžete definovat a používat obecné procedury. Viz [Obecné procedury v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Výhody obecných typů  
 Obecný typ slouží jako základ pro deklarování několika různých programovacích prvků, z nichž každý pracuje na konkrétním datovém typu. Alternativy obecného typu jsou:  
  
1. Jeden typ, který pracuje na datovém typu `Object`.  
  
2. Sada verzí typu *specifických pro konkrétní typ* , každá verze se individuálně nakóduje a pracuje na jednom konkrétním datovém typu, jako je `String`, `Integer`nebo uživatelsky definovaný typ, jako je `customer`.  
  
 Obecný typ má oproti těmto alternativám následující výhody:  
  
- **Bezpečnost typů.** Obecné typy vynutily kontrolu typu při kompilaci. Typy založené na `Object` přijímají libovolný datový typ a musíte napsat kód, abyste zkontrolovali, jestli je vstupní datový typ přijatelný. S obecnými typy může kompilátor zachytit neshodu typu před časem spuštění.  
  
- **Předepsané.** Obecné typy nejsou k dispozici pro *pole* a *unbox* dat, protože každá z nich je specializovaná pro jeden datový typ. Operace založené na `Object` musí být zapsány vstupními datovými typy, aby je bylo možné převést na `Object` a unbox data určená pro výstup. Zabalení a rozbalení sníží výkon.  
  
     Typy založené na `Object` jsou také pozdní vazbou, což znamená, že přístup ke svým členům vyžaduje za běhu další kód. Tím se také snižuje výkon.  
  
- **Konsolidace kódu.** Kód v obecném typu musí být definován pouze jednou. Sada verzí typu specifických pro typ musí replikovat stejný kód v každé verzi, přičemž jediným rozdílem je konkrétní datový typ pro danou verzi. S obecnými typy jsou verze specifické pro typ vygenerovány z původního obecného typu.  
  
- **Opětovné použití kódu.** Kód, který není závislý na konkrétním datovém typu, lze znovu použít s různými datovými typy, pokud je obecný. Můžete ji často použít i s datovým typem, který jste nepůvodně předpovídat.  
  
- **Podpora IDE.** Když použijete konstruovaný typ deklarovaný z obecného typu, integrované vývojové prostředí (IDE) vám může poskytnout větší podporu při vývoji kódu. Například IntelliSense může zobrazit možnosti specifické pro argument pro konstruktor nebo metodu.  
  
- **Obecné algoritmy** Abstraktní algoritmy, které jsou nezávislé na typu, jsou vhodnými kandidáty pro obecné typy. Například obecný postup, který Seřadí položky pomocí rozhraní <xref:System.IComparable>, lze použít s jakýmkoli datovým typem, který implementuje <xref:System.IComparable>.  
  
## <a name="constraints"></a>Omezení  
 I když kód v definici obecného typu by měl být nezávisle na typu, možná budete muset vyžadovat určitou funkci libovolného datového typu, který je součástí vašeho obecného typu. Například pokud chcete porovnat dvě položky pro účely řazení nebo kompletování, jejich datový typ musí implementovat rozhraní <xref:System.IComparable>. Tento požadavek můžete vyhovět přidáním *omezení* do parametru typu.  
  
### <a name="example-of-a-constraint"></a>Příklad omezení  
 Následující příklad ukazuje kostru třídy s omezením, které vyžaduje, aby argument typu implementoval <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#5)]  
  
 Pokud se další kód pokusí sestavit třídu z `itemManager` zadání typu, který neimplementuje <xref:System.IComparable>, kompilátor signalizuje chybu.  
  
### <a name="types-of-constraints"></a>Typy omezení  
 Vaše omezení může v libovolné kombinaci zadat následující požadavky:  
  
- Argument typu musí implementovat jedno nebo víc rozhraní.  
  
- Argument typu musí být typu nebo dědit od, maximálně jedné třídy.  
  
- Argument typu musí zveřejnit konstruktor bez parametrů přístupný kódu, který vytváří objekty z něj.  
  
- Argument typu musí být *typ odkazu*, nebo musí být *typ hodnoty* .  
  
 Pokud potřebujete zavést více než jeden požadavek, použijte *seznam omezení* oddělený čárkami ve složených závorkách (`{ }`). Pro vyžadování přístupového konstruktoru zahrnete klíčové slovo [new operátoru](../../../../visual-basic/language-reference/operators/new-operator.md) v seznamu. Chcete-li vyžadovat odkazový typ, zahrňte klíčové slovo `Class`; Chcete-li vyžadovat typ hodnoty, zahrňte klíčové slovo `Structure`.  
  
 Další informace o omezeních najdete v tématu [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Příklad více omezení  
 Následující příklad ukazuje kostru definice obecné třídy se seznamem omezení v parametru typu. V kódu, který vytváří instanci této třídy, musí argument typu implementovat rozhraní <xref:System.IComparable> i <xref:System.IDisposable>, být odkazový typ a vystavit přístupný konstruktor bez parametrů.  
  
 [!code-vb[VbVbalrDataTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#6)]  
  
## <a name="important-terms"></a>Důležité výrazy  
 Obecné typy představují a používají následující výrazy:  
  
- *Obecný typ* Definice třídy, struktury, rozhraní, procedury nebo delegáta, pro který zadáte alespoň jeden datový typ při jeho deklaraci.  
  
- *Parametr typu* V definici obecného typu je zástupný symbol pro datový typ, který zadáte při deklaraci typu.  
  
- *Argument typu* Konkrétní datový typ, který nahradí parametr typu při deklaraci vytvořeného typu z obecného typu.  
  
- *Omezení*. Podmínka u parametru typu, který omezuje argument typu, který můžete pro něj zadat. Omezení může vyžadovat, aby argument typu vyžadoval implementaci konkrétního rozhraní, nebo dědění z konkrétní třídy, mít přístupný konstruktor bez parametrů, nebo jako typ odkazu nebo typ hodnoty. Tato omezení můžete kombinovat, ale můžete zadat maximálně jednu třídu.  
  
- *Konstruovaný typ*. Třída, struktura, rozhraní, procedura nebo delegát deklarované z obecného typu zadáním argumentů typu pro jeho parametry typu.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Tohoto](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Formátu](../../../../visual-basic/language-reference/statements/as-clause.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Kovariance a kontravariance](../../concepts/covariance-contravariance/index.md)
- [Iterátory](../../../../visual-basic/programming-guide/concepts/iterators.md)
