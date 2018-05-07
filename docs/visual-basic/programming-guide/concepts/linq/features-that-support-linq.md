---
title: Funkce Visual Basic podporující LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: db2eff2f7c19a3c510e7b212f5bb406d7a885439
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-features-that-support-linq"></a>Funkce Visual Basic podporující LINQ
Název [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] odkazuje technologie v jazyce Visual Basic, podporuje syntaxe dotazu a dalších jazyků vytvoří přímo v jazyce. S [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], není nutné další informace o nový jazyk k dotazu vůči externího zdroje dat. Můžete dotazovat na data v relačních databází, úložiště XML nebo objekty v jazyce Visual Basic. Tato integrace možnosti dotazu do jazyka umožňuje kompilaci kontrola chyby syntaxe a bezpečnost typů. Tato integrace zajišťuje již znáte většinu co musíte vědět, abyste mohli psát dotazy bohatou a rozmanitých v jazyce Visual Basic.  
  
 Následující části popisují jazykové konstrukty, které podporují LINQ v dostatek podrobností, které se vám umožní začít pracovat v úvodní dokumentaci, příklady kódu a ukázkové aplikace. Můžete také kliknutím na odkazy najít více podrobné vysvětlení, jak použít jazykové funkce současně povolit language-integrated query. Je vhodné oddělení na zahájení [návod: zápis dotazů v jazyce Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Výrazy dotazu  
 Výrazy dotazů v jazyce Visual Basic, může být vyjádřený v deklarativní syntaxi, která je podobná SQL nebo XQuery. Při kompilaci syntaxe dotazu je převést na volání metody pro implementaci zprostředkovatele LINQ metod rozšíření operátor standardní dotazu. Řízení aplikace, které standardní operátory dotazu, které se nacházejí v oboru tak, že zadáte odpovídající oboru názvů s `Imports` příkaz. Syntaxe výrazu dotazu jazyka Visual Basic vypadá takto:  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Další informace najdete v tématu [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Implicitně Typovaná proměnné  
 Místo explicitním zadáním typu, pokud deklarace a inicializace proměnné, můžete povolit kompilátoru odvození a typ přiřazení. Tento proces se označuje jako *odvození místního typu*.  
  
 Proměnné jsou odvodit, jejichž typy jsou silného typu, stejně jako proměnné s typem explicitně zadáte. Odvození místního typu funguje jenom v případě, že definujete proměnnou místní uvnitř těla metody. Další informace najdete v tématu [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Následující příklad ilustruje odvození místního typu. Pokud chcete použít v tomto příkladu, je nutné nastavit `Option Infer` k `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Odvození místního typu také umožňuje vytvářet anonymní typy, které jsou popsané dál v této části a jsou nutné pro dotazy LINQ.  
  
 V následujícím příkladu LINQ odvození typu dojde, pokud `Option Infer` je buď `On` nebo `Off`. Pokud dojde k chybě kompilace `Option Infer` je `Off` a `Option Strict` je `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Inicializátory objektů  
 Inicializátory objektů se používají ve výrazech dotazů, když budete muset vytvořit instanci anonymního typu k ukládání výsledků dotazu. Také můžete používají třeba inicializovat objekty pojmenované typy mimo dotazy. Pomocí inicializátoru objektů můžete inicializovat objekt na jediném řádku bez nutnosti explicitně volání konstruktoru. Za předpokladu, že máte třídy s názvem `Customer` má veřejné `Name` a `Phone` vlastnosti, společně s další vlastnosti inicializátoru objektu je možné tímto způsobem:  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Další informace najdete v tématu [inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typy poskytnout vhodný způsob k dočasně seskupení sadu vlastností do element, který chcete zahrnout do výsledku dotazu. To můžete zvolit libovolnou kombinaci dostupná pole v dotazu v libovolném pořadí, bez definování pojmenované datový typ pro element.  
  
 *Anonymní typ* sestavený kompilátor dynamicky. Název typu je přiřazena službou kompilátor a mohou změnit s každou nové kompilace. Název proto nelze použít přímo. Anonymní typy jsou inicializovány následujícím způsobem:  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Další informace najdete v tématu [anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozšíření  
 Rozšiřující metody umožňují přidejte metody na datový typ nebo mimo definici rozhraní. Tato funkce umožňuje, platí, přidat nové metody do existujícího typu beze změny ve skutečnosti typu. Standardní operátory dotazu jsou sami sady rozšiřující metody, které poskytují [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz funkce pro žádný typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. Další rozšíření pro <xref:System.Collections.Generic.IEnumerable%601> zahrnují <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, a <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 Následující metody rozšíření přidá tiskové způsob <xref:System.String> třídy.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 Metoda je volána jako metodu obyčejnou instance z <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Další informace najdete v tématu [rozšiřující metody](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Výrazy lambda  
 Výraz lambda je funkce, bez název, který vypočítá a vrátí jednu hodnotu. Na rozdíl od funkce s názvem mohou být výraz lambda definované a provedeny ve stejnou dobu. Následující příklad zobrazuje 4.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Můžete přiřadit definici výrazu lambda název proměnné a pak použít název pro volání funkce. Tento příklad také zobrazuje 4.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 V [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], výrazů lambda tvoří základ řadu standardní operátory dotazu. Lambda – výrazy k zachycení výpočty, které jsou definovány v metody základní dotazů, jako například vytvoří kompilátor `Where`, `Select`, `Order By`, `Take While`a další.  
  
 Například následující kód definuje dotaz, který vrátí všechny pokročilých studentů ze seznamu studenty.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 Definice dotazu zkompilován kód, který je podobně jako v následujícím příkladu, který používá dvou výrazů lambda Pokud chcete zadat argumenty pro `Where` a `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Buď verze můžete spustit pomocí `For Each` smyčka:  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Další informace najdete v tématu [výrazy Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Viz také  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ a řetězce (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Příkaz Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
