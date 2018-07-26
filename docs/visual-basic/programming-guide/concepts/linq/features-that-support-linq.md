---
title: Funkce Visual Basic podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: db2eff2f7c19a3c510e7b212f5bb406d7a885439
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199144"
---
# <a name="visual-basic-features-that-support-linq"></a>Funkce Visual Basic podporující LINQ
Název [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] odkazuje na technologie v jazyce Visual Basic, že podporuje syntaxi dotazu a jiné jazykové konstrukty přímo v jazyce. S [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], nemusíte učit nový jazyk k dotazu vůči externímu zdroji dat. V jazyce Visual Basic můžete dotazovat data v relačních databází, úložiště XML nebo objekty. Tato integrace možností dotazování jazyk povolí kompilaci kontrolu pro chyby syntaxe a bezpečnost typů. Tato integrační také zajišťuje, že už znáte většinu toho, co máte vědět o zápis bohatě vybaveným a různých dotazů v jazyce Visual Basic.  
  
 Následující části popisují jazykovým konstrukcím, které podporují LINQ dostatečně podrobně, aby vám umožní začít během čtení úvodní dokumentaci, ukázky kódu a ukázkové aplikace. Můžete také kliknutím na odkazy najdete podrobnější vysvětlení jak jazykové funkce setkávají, aby se povolit jazyka integrované dotazu. Je dobrým začátkem [návod: zápis dotazů v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Výrazy dotazu  
 Výrazy dotazů v jazyce Visual Basic lze vyjádřit v deklarativní syntaxe podobná SQL nebo výraz XQuery. V době kompilace je syntaxe dotazu převeden na volání metody k implementaci zprostředkovatele LINQ standardní metody operátoru dotazu rozšíření. Řízení aplikací, které jsou operátory standardního dotazu v oboru tak, že zadáte odpovídající obor názvů s `Imports` příkazu. Syntaxe výrazu dotazu jazyka Visual Basic vypadá takto:  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Další informace najdete v tématu [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Implicitně typované proměnné  
 Namísto explicitního určení typu, když deklarujete a inicializujete proměnnou, můžete povolit kompilátor odvodit a přiřadit typu. To se označuje jako *odvození místního typu*.  
  
 Proměnné, jejichž typy jsou odvozeny jsou silného typu, stejně jako proměnné, jejíž typ zadat explicitně. Odvození místního typu funguje pouze v případě, že definujete lokální proměnná uvnitř těla metody. Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Následující příklad ukazuje odvození místního typu. Pokud chcete použít tento příklad, je nutné nastavit `Option Infer` k `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Odvození místního typu také umožňuje vytvořit anonymní typy, které jsou popsané dále v této části a jsou nutné pro dotazy LINQ.  
  
 V následujícím příkladu LINQ, dojde k odvození typu Pokud `Option Infer` je buď `On` nebo `Off`. Pokud dojde k chybě kompilace `Option Infer` je `Off` a `Option Strict` je `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Inicializátory objektů  
 Inicializátory objektů se používají ve výrazech dotazů, když máte k vytvoření anonymního typu k ukládání výsledků dotazu. Můžete se používají také k inicializaci objektů třídy pojmenované typy mimo dotazy. S použitím inicializátoru objektu, můžete inicializovat objekt na jednom řádku bez nutnosti explicitně volat konstruktor. Za předpokladu, že máte třídu s názvem `Customer` , která má veřejný `Name` a `Phone` vlastnosti, společně s další vlastnosti inicializátoru objektu je možné tímto způsobem:  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Další informace najdete v tématu [inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typy poskytují pohodlný způsob, aby dočasně seskupily sadu vlastností do elementu, který chcete zahrnout do výsledku dotazu. To můžete zvolit libovolnou kombinaci dostupných polí v dotazu, v libovolném pořadí, bez definování pojmenované datový typ pro element.  
  
 *Anonymního typu* je dynamicky vytvořený kompilátorem. Název typu je přiřazena kompilátorem a může změnit s každou novou kompilaci. Název proto nelze použít přímo. Anonymní typy jsou inicializovány v následujícím způsobem:  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozšíření  
 Rozšiřující metody umožňují přidat metody datového typu nebo mimo definici rozhraní. Tato funkce umožňuje, v důsledku toho přidejte nové metody k existujícímu typu beze změny ve skutečnosti typu. Operátory standardního dotazu představují samy o sobě sadu rozšiřujících metod, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazování funkce pro libovolný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. Další rozšíření pro <xref:System.Collections.Generic.IEnumerable%601> zahrnují <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, a <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 Následující metody rozšíření přidá tisku metodu <xref:System.String> třídy.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 Metoda je volána jako o běžnou metodu instance z <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Další informace najdete v tématu [rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 Výraz lambda je funkce bez názvu, který vypočítá a vrátí jednu hodnotu. Na rozdíl od funkce s názvem mohou být výraz lambda definován a provedeny ve stejnou dobu. Následující příklad zobrazuje 4.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Můžete přiřadit definici výrazu lambda s názvem proměnné a pak použijte název pro volání funkce. Následující příklad zobrazuje také 4.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], výrazů lambda tvoří základ mnoho standardních operátorů pro dotazování. Kompilátor vytvoří výrazy lambda zachycení výpočty, které jsou definovány metody základních dotazů jako například `Where`, `Select`, `Order By`, `Take While`a další.  
  
 Například následující kód definuje dotaz, který vrátí vedoucí Všichni studenti ze seznamu studentů.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 Definice dotazu je zkompilováno do kódu, který je podobný následujícím příkladu, který se používá k určení argumentů dvou výrazů lambda `Where` a `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Buď verze můžete spustit pomocí `For Each` smyčka:  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Další informace najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
