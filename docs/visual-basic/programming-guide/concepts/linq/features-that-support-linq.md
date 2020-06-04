---
title: Funkce, které podporují LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 15585cd8277b1a0df7e3b262db7c9b7a231b16fa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383427"
---
# <a name="visual-basic-features-that-support-linq"></a>Funkce Visual Basic podporující LINQ
Názvový jazyk integrovaný dotaz (LINQ) odkazuje na technologii v Visual Basic, která podporuje syntaxi dotazů a jiné jazykové konstrukce přímo v jazyce. Pomocí LINQ se nemusíte učit nový jazyk a dotazovat se na externí zdroj dat. Pomocí Visual Basic můžete zadávat dotazy na data v relačních databázích, v úložištích XML nebo v objektech. Tato integrace možností dotazů do jazyka umožňuje v době kompilace provádět kontrolu chyb syntaxe a zabezpečení typů. Tato integrace také zajišťuje, že už znáte většinu toho, co potřebujete znát k psaní bohatých a proměnlivých dotazů v Visual Basic.  
  
 V následujících částech jsou popsány jazykové konstrukce, které podporují LINQ dostatečně podrobně, aby bylo možné začít číst úvodní dokumentaci, příklady kódu a ukázkové aplikace. Můžete také kliknout na odkazy a najít podrobnější vysvětlení způsobu, jakým jsou tyto funkce jazyka spojeny, a umožnit tak dotaz integrovaný do jazyka. Dobrým místem pro začátek je [Návod: zápis dotazů v Visual Basic](walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Výrazy dotazu  
 Výrazy dotazů v Visual Basic lze vyjádřit v deklarativní syntaxi podobné řetězci jazyka SQL nebo XQuery. V době kompilace se syntaxe dotazu převádí na volání metody do implementace metod rozšíření standardních operátorů dotazů zprostředkovatele LINQ. Aplikace řídí, které standardní operátory dotazu jsou v oboru, zadáním příslušného oboru názvů pomocí `Imports` příkazu. Syntaxe výrazu dotazu Visual Basic vypadá takto:  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 Další informace najdete v tématu [Úvod do LINQ v Visual Basic](../../language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Implicitně typované proměnné  
 Namísto explicitního určení typu při deklaraci a inicializaci proměnné můžete povolit kompilátoru, aby odvodit a přidělil typ. To se označuje jako *odvození místního typu*.  
  
 Proměnné, jejichž typy jsou odvozeny, jsou silně typované, stejně jako proměnné, jejichž typ zadáte explicitně. Odvození místního typu funguje pouze v případě, že definujete místní proměnnou uvnitř těla metody. Další informace naleznete v tématu [možnost odvození příkazu](../../../language-reference/statements/option-infer-statement.md) a [odvození místního typu](../../language-features/variables/local-type-inference.md).  
  
 Následující příklad znázorňuje odvození místního typu. Chcete-li použít tento příklad, musíte nastavit `Option Infer` na `On` .  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 Odvození místního typu také umožňuje vytvořit anonymní typy, které jsou popsány dále v této části a jsou nezbytné pro dotazy LINQ.  
  
 V následujícím příkladu LINQ dojde k odvození typu, pokud `Option Infer` je buď `On` nebo `Off` . Pokud je a, dojde k chybě při kompilaci `Option Infer` `Off` `Option Strict` `On` .  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>Inicializátory objektů  
 Inicializátory objektů se používají ve výrazech dotazů, pokud je třeba vytvořit anonymní typ pro uložení výsledků dotazu. Lze je také použít k inicializaci objektů pojmenovaných typů mimo dotazy. Pomocí inicializátoru objektu můžete inicializovat objekt v jednom řádku bez explicitního volání konstruktoru. Za předpokladu, že máte třídu s názvem `Customer` , která má veřejné `Name` a `Phone` vlastnosti spolu s dalšími vlastnostmi, lze použít inicializátor objektu tímto způsobem:  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 Další informace naleznete v tématu [Inicializátory objektů: pojmenované a anonymní typy](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Anonymní typy  
 Anonymní typy poskytují pohodlný způsob, jak dočasně seskupit sadu vlastností do prvku, který chcete zahrnout do výsledku dotazu. Díky tomu můžete zvolit libovolnou kombinaci dostupných polí v dotazu, a to v libovolném pořadí, aniž byste definovali pojmenovaný datový typ pro element.  
  
 *Anonymní typ* je dynamicky sestaven kompilátorem. Název typu je přiřazen kompilátorem a může se změnit u každé nové kompilace. Proto název nelze použít přímo. Anonymní typy jsou inicializovány následujícím způsobem:  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 Další informace najdete v tématu [anonymní typy](../../language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozšíření  
 Metody rozšíření umožňují přidat metody do datového typu nebo rozhraní mimo definici. Tato funkce vám umožňuje přidat nové metody do existujícího typu, aniž by bylo nutné upravovat typ. Standardní operátory dotazu jsou vlastní sadou rozšiřujících metod, které poskytují funkce dotazů LINQ pro jakýkoli typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> . Další rozšíření pro <xref:System.Collections.Generic.IEnumerable%601> zahrnutí <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.Union%2A> a <xref:System.Linq.Enumerable.Intersect%2A> .  
  
 Následující metoda rozšíření přidá do třídy metodu Print <xref:System.String> .  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 Metoda je volána jako Obvyklá metoda instance pro <xref:System.String> :  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 Další informace naleznete v tématu [metody rozšíření](../../language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Lambda – výrazy  
 Výraz lambda je funkce bez názvu, který počítá a vrací jedinou hodnotu. Na rozdíl od pojmenovaných funkcí lze definovat a spustit výraz lambda ve stejnou dobu. Následující příklad zobrazí 4.  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 Definici výrazu lambda můžete přiřadit názvu proměnné a potom použít název pro volání funkce. V následujícím příkladu se zobrazí také 4.  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 V LINQ jsou výrazy lambda základem mnoha standardních operátorů dotazu. Kompilátor vytvoří výrazy lambda pro zachycení výpočtů, které jsou definovány v základních metodách dotazů, jako jsou,,, `Where` `Select` `Order By` `Take While` a další.  
  
 Například následující kód definuje dotaz, který vrátí všechny vyšší studenty ze seznamu studentů.  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 Definice dotazu je zkompilována do kódu, který je podobný následujícímu příkladu, který používá dva výrazy lambda pro určení argumentů pro `Where` a `Select` .  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 Obě verze je možné spustit pomocí `For Each` smyčky:  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 Další informace naleznete v tématu [lambda výrazy](../../language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Viz také

- [LINQ (Language-Integrated Query) (Visual Basic)](index.md)
- [Začínáme s dotazy LINQ v jazyce Visual Basic](getting-started-with-linq.md)
- [LINQ a řetězce (Visual Basic)](linq-and-strings.md)
- [Option Infer – příkaz](../../../language-reference/statements/option-infer-statement.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
