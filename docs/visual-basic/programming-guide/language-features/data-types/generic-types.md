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
ms.openlocfilehash: f86819f9bd3cbcceb4be696852655018868f4a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Obecné typy v jazyce Visual Basic (Visual Basic)
A *obecného typu* je jeden programovací element, který přizpůsobí provádět stejné funkce pro různé datové typy. Při definování obecné třídy nebo postup nemáte definovat samostatné verze pro každý typ dat, pro které můžete chtít provést této funkce.  
  
 Sledují se šroubováku s vyměnitelné oznámení. Zkontrolujte šroubovacím, budete muset zapnout a vyberte správnou hlavičku pro tento šroub (s drážkou, překročí, starred). Jakmile můžete vložit správné head šroubovák popisovač, provedete přesně stejnou funkci s šroubovák, konkrétně vypnutí šroubek.  
  
 ![Diagram šroubováku jako obecný nástroj](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
Šroubováku jako obecný nástroj  
  
 Při definování obecného typu Parametrizace s jeden nebo více datových typů. To umožňuje použití kódu můžete nastavit typy dat, které mají požadavky na jeho. Váš kód můžou deklarovat několik různých programovací elementy ze obecné elementu, každé z nich funguje na jinou sadu datových typů. Ale deklarované elementy všechny provádět stejné logiky, bez ohledu na to, jaké typy dat používají.  
  
 Například můžete chtít vytvořit a použít fronty třídu, která funguje na určité datový typ jako `String`. Je možné deklarovat třídy z <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 Teď můžete použít `stringQ` pracovat pouze s `String` hodnoty. Protože `stringQ` je specifický pro `String` místo se zobecněn pro `Object` hodnoty, není nutné pozdní vazba nebo typ převodu. Tím ušetříte čas spuštění a snižuje běhové chyby.  
  
 Další informace o použití obecného typu, najdete v části [postupy: použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).  
  
## <a name="example-of-a-generic-class"></a>Příklad obecné třídy  
 Následující příklad ukazuje definici kostru obecné třídy.  
  
 [!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 V předchozím kostru `t` je *parametr typu*, který je zástupný symbol pro datový typ, který zadáte po deklarování třídy. Někde v kódu, můžou deklarovat různých verzích `classHolder` zadáním různé datové typy pro `t`. Následující příklad ukazuje dva tato prohlášení.  
  
 [!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 Předchozí příkazy deklarovat *sestavený třídy*, ve kterém konkrétního typu nahrazuje parametr typu. Tato nahrazení je šíření v kódu v rámci sestavené třídy. Následující příklad ukazuje, co `processNewItem` postup vypadá jako v `integerClass`.  
  
 [!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 Více kompletní příklad najdete v tématu [postupy: definování třídy, můžete zadat identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).  
  
## <a name="eligible-programming-elements"></a>Oprávněné programovací elementy  
 Můžete definovat a použití obecné třídy, struktury, rozhraní, postupy a delegáti. Všimněte si, že [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definuje několik obecných tříd, struktur a rozhraní, které představují běžně používané obecné elementy. <xref:System.Collections.Generic?displayProperty=nameWithType> Obor názvů obsahuje slovník, seznamů, front a zásobníky. Před definováním vlastního obecné elementu, zkontrolujte, jestli je již k dispozici v <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
 Postupy nejsou typy, ale můžete definovat a použijte obecné procedury. V tématu [obecné procedury v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).  
  
## <a name="advantages-of-generic-types"></a>Výhody obecných typů  
 Obecný typ slouží jako základ pro deklarování několik různých programovací prvky, z nichž každý funguje na určité datový typ. Alternativy k obecného typu jsou:  
  
1.  Jeden typ pracující na `Object` datového typu.  
  
2.  Sadu *specifický* verze typu jednotlivých verzí jednotlivě programového a pracující na typu jeden konkrétní data, jako `String`, `Integer`, nebo uživatelsky definovaný typ. například `customer`.  
  
 Obecný typ má následující výhody přes tyto možnosti:  
  
-   **Zabezpečení typů.** Obecné typy vynutit kontrola typu v kompilaci. Na základě typů `Object` přijměte jakýkoli datový typ a musíte napsat kód a zkontrolujte, zda typ vstupních dat. přijatelný. S obecné typy můžete kompilátor catch neshody typu než čas spuštění.  
  
-   **Výkon.** Obecné typy nemusíte *pole* a *unbox* data, protože každé z nich se specializuje na jednoho datového typu. Na základě operace `Object` musí pole vstupních dat typy převést tak, aby `Object` a unbox dat určený pro výstup. Zabalení a rozbalení snížit výkon.  
  
     Na základě typů `Object` jsou také pozdní vazby, což znamená, že přístup k jejich členové vyžaduje další kódu v době běhu. To také snižuje výkon.  
  
-   **Konsolidace kódu.** Kód v obecného typu musí být definovaný jenom jednou. Sadu typ specifické verze typu musí replikovat stejný kód v jednotlivých verzích s jediným rozdílem je konkrétní datový typ pro tuto verzi. S obecné typy jsou všechny verze specifický generovány z původní obecného typu.  
  
-   **Opakované použití kódu.** Pokud je obecný lze znovu kód, který není závislá na datový typ. použít s různými datovými typy. Můžete je často opakují i s datový typ, který jste není předpovědi původně.  
  
-   **Podpora rozhraní IDE.** Pokud používáte vytvořený typ deklarovaný od obecného typu, integrované vývojové prostředí (IDE) vám může poskytnout další podporu při vývoji vašeho kódu. IntelliSense můžete můžete například zobrazit možnosti specifický pro argument metoda nebo konstruktor.  
  
-   **Obecné algoritmy.** Abstraktní algoritmy, které jsou nezávislé na typ jsou vhodnými kandidáty pro obecné typy. Například obecné procedury, která Seřadí položky pomocí <xref:System.IComparable> rozhraní lze použít s datovým typem, který implementuje <xref:System.IComparable>.  
  
## <a name="constraints"></a>Omezení  
 I když kód v definici obecného typu by měl být jako typ nezávislé nejblíže, můžete vyžadovat určité funkce jakýkoli datový typ zadaný do obecného typu. Například pokud chcete k porovnání dvou položek za účelem řazení nebo kompletování, jejich datový typ musí implementovat <xref:System.IComparable> rozhraní. Tento požadavek můžete vynutit přidáním *omezení* typ parametru.  
  
### <a name="example-of-a-constraint"></a>Příklad omezení  
 Následující příklad ukazuje definici kostru třídy s omezením, která vyžaduje argument typu k implementaci <xref:System.IComparable>.  
  
 [!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 Pokud následné kódu se pokusí vytvořit třídu z `itemManager` se zadaným typem, který neimplementuje <xref:System.IComparable>, kompilátor nevydá signál k chybě.  
  
### <a name="types-of-constraints"></a>Typy omezení  
 Vaše omezení v libovolné kombinace můžete určit následující požadavky:  
  
-   Argument typu musí implementovat jednu nebo více rozhraní  
  
-   Argument typu musí být typu, nebo nastavte dědičnost z maximálně jednu třídu  
  
-   Argument typu musí vystavit přístupné pro kód, který vytvoří objekty z něj konstruktor bez parametrů  
  
-   Argument typu musí být *odkazují na typ*, nebo musí být *typu hodnoty*  
  
 Pokud potřebujete použít více než jeden požadavek, můžete použít oddělené čárkami *seznamu omezení* uvnitř složené závorky (`{ }`). Pokud chcete vyžadovat dostupný konstruktor, zahrnete [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo v seznamu. Pokud chcete vyžadovat typu odkazu, zahrnete `Class` – klíčové slovo; tak, aby vyžadovala typu hodnoty zahrnete `Structure` – klíčové slovo.  
  
 Další informace o omezení najdete v tématu [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).  
  
### <a name="example-of-multiple-constraints"></a>Příklad více omezení  
 Následující příklad ukazuje definici kostru obecné třídy s seznamu omezení na parametr typu. V kódu, který vytvoří instanci této třídy, musí implementovat argument typu i <xref:System.IComparable> a <xref:System.IDisposable> rozhraní, být odkazového typu a vystavit přístupné bezparametrový konstruktor.  
  
 [!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a>Důležité termíny  
 Obecné typy zavést a používají následující termíny:  
  
-   *Obecný typ*. Definice třídy, struktury, rozhraní, postup nebo delegáta, pro kterou je zadat nejméně jeden datový typ při jeho deklaraci.  
  
-   *Zadejte parametr*. V definici obecného typu zástupný symbol pro datový typ je zadat při deklaraci typu.  
  
-   *Argument typu*. Konkrétní datový typ, který nahrazuje parametr typu při deklaraci typu vytvořený z obecného typu.  
  
-   *Omezení*. Podmínkou na parametr typu, který omezuje argument typu můžete zadat pro něj. Omezení může vyžadovat, aby argument typu musí implementovat určité rozhraní, se konkrétní třídy dědí, mít dostupný konstruktor nebo být odkazového typu nebo typ hodnoty. Zkombinováním těchto omezení, ale můžete zadat maximálně jednu třídu.  
  
-   *Vytvořený typ*. Třída, struktura, rozhraní, postup nebo delegáta deklarovat zadáním argumenty typu pro jeho parametry typu od obecného typu.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [z](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [jako](../../../../visual-basic/language-reference/statements/as-clause.md)  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Kovariance a kontravariance](../../concepts/covariance-contravariance/index.md)  
 [Iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
