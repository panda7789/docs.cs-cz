---
title: Obory názvů v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ec038a17b4a6b10dbe339fe33969c4ade57e2a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="namespaces-in-visual-basic"></a>Obory názvů v jazyce Visual Basic
Obory názvů uspořádat objekty definované v sestavení. Sestavení může obsahovat více obory názvů, který zase mohou obsahovat jiných oborech názvů. Obory názvů zabránilo nejednoznačnosti a zjednodušit odkazy, při použití velké skupiny objektů, například knihovny tříd.  
  
 Například [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] definuje <xref:System.Windows.Forms.ListBox> třídy v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů. Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaný název pro tuto třídu:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Zamezení kolize názvů  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obory názvů vyřešit problém se někdy označuje jako *znečištění oboru názvů*, ve které je na vývojáře knihovny tříd pomocí podobné názvy v jiné knihovny omezován. Tyto je v konfliktu s existující součásti se někdy označuje jako *název kolizí*.  
  
 Například pokud vytvoříte novou třídu s názvem `ListBox`, můžete ji použít v projektu bez kvalifikace. Ale pokud chcete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> třídy ve stejném projektu, musíte použít plně kvalifikovaný odkaz aby jedinečný odkaz. Pokud není jedinečný odkaz, vyvolá jazyka Visual Basic chyba oznamující, že název je nejednoznačný. Následující příklad kódu ukazuje, jak deklarovat tyto objekty:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 Následující obrázek znázorňuje dvěma hierarchiemi obor názvů, jak obsahuje objekt s názvem `ListBox`.  
  
 ![Namespace hierarchie](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Ve výchozím nastavení obsahuje každý spustitelný soubor, který vytvoříte v jazyce Visual Basic obor názvů se stejným názvem jako projektu. Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject`, spustitelný soubor ListBoxProject.exe obsahuje obor názvů s názvem `ListBoxProject`.  
  
 Více sestavení můžete použít stejný obor názvů. Visual Basic je považuje za jednu sadu názvy. Například můžete definovat třídy pro obor názvů s názvem `SomeNameSpace` v sestavení s názvem `Assemb1`a definovat další třídy pro stejného oboru názvů ze sestavení s názvem `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy  
 Plně kvalifikované názvy jsou odkazy na objekty, které mají předponu název oboru názvů, ve kterém je definovaný objekt. Můžete použít objekty, které jsou definovány v jiné projekty, je-li vytvořit odkaz na třídu (výběrem **přidat odkaz na** z **projektu** nabídky) a pak použít plně kvalifikovaný název objektu v kódu. Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název pro objekt z jiného projektu názvů:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Plně kvalifikované názvy zabránit pojmenování konfliktu, protože možnost pro kompilátor k určení, který objekt je používán. Názvy sami, můžete však získat dlouhé a komplikované. Chcete-li se tomuto problému vyhnout, můžete použít `Imports` příkaz k definování *alias*– zkrácený název budete moct používat místo plně kvalifikovaný název. Například následující příklad kódu vytvoří aliasy pro dvě plně kvalifikované názvy a používá tyto aliasy pro definování dva objekty.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Pokud použijete `Imports` příkaz bez alias, můžete použít všechny názvy v tom, že zadaný obor názvů bez kvalifikace, jsou jedinečné pro projekt. Pokud projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, musíte plně před tímto názvem pokud ji používáte. Předpokládejme například projektu obsažena následující dva `Imports` příkazy:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Pokud pokus o použití `Class1` bez plně kvalifikovaného, Visual Basic vytvoří chybu oznamující, že název `Class1` je nejednoznačný.  
  
## <a name="namespace-level-statements"></a>Úroveň Namespace příkazy  
 V oboru názvů můžete definovat položek, jako jsou moduly, rozhraní, třídy, delegáti, struktury, výčty a jiných oborech názvů. Nelze definovat položek, jako jsou vlastnosti, postupy, proměnné a události na úrovni oboru názvů. Tyto položky musí být deklarován v rámci kontejnery, jako jsou moduly, struktury nebo třídy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Global – klíčové slovo ve plně kvalifikované názvy  
 Pokud jsou definovány vnořené hierarchie oborů názvů, kód v této hierarchii mohou blokovat přístup k <xref:System?displayProperty=nameWithType> obor názvů rozhraní .NET Framework. Následující příklad ilustruje hierarchie, ve kterém `SpecialSpace.System` obor názvů blokuje přístup k <xref:System?displayProperty=nameWithType>.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 V důsledku toho kompilátoru jazyka Visual Basic nelze úspěšně vyhodnotit odkaz na <xref:System.Int32?displayProperty=nameWithType>, protože `SpecialSpace.System` nedefinuje `Int32`. Můžete použít `Global` – klíčové slovo zahájíte řetězu kvalifikace na úrovni nejkrajnější knihovně tříd rozhraní .NET Framework. Umožňuje zadat <xref:System?displayProperty=nameWithType> oboru názvů nebo jiný obor názvů v knihovně tříd. Toto dokládá následující příklad.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Můžete použít `Global` do jiných oborech názvů kořenové úrovně přístupu, jako například <xref:Microsoft.VisualBasic?displayProperty=nameWithType>a obor názvů přidružené k projektu.  
  
## <a name="global-keyword-in-namespace-statements"></a>Global – klíčové slovo v příkazech Namespace  
 Můžete také `Global` – klíčové slovo v [příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). To umožňuje definovat oboru názvů z kořenového oboru názvů vašeho projektu.  
  
 Všechny obory názvů v projektu jsou založené na kořenového oboru názvů pro projekt.  Visual Studio přiřadí název projektu jako výchozí kořenový obor názvů pro všechny kódu v projektu. Například pokud je název projektu `ConsoleApplication1`, jeho programovací elementy patří do oboru názvů `ConsoleApplication1`. Pokud je deklarovat `Namespace Magnetosphere`, odkazuje na `Magnetosphere` v projektu budou přistupovat k `ConsoleApplication1.Magnetosphere`.  
  
 Následující příklady použití `Global` – klíčové slovo k deklaraci oboru názvů z kořenového oboru názvů pro projekt.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 V deklaraci oboru názvů `Global` nelze vnořit v jiném oboru názvů.  
  
 Můžete použít [stránka aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) zobrazovat a upravovat **kořenové Namespace** projektu.  Pro nové projekty **kořenové Namespace** výchozí hodnota je název projektu. Způsobí `Global` na nejvyšší úrovni oboru názvů, můžete vymazat **kořenové Namespace** položky tak, aby pole je prázdné. Vymazání **kořenové Namespace** odebírá potřebu, `Global` – klíčové slovo v deklarace oboru názvů.  
  
 Pokud `Namespace` příkaz deklaruje název, který je taky obor názvů v rozhraní .NET Framework, obor názvů rozhraní .NET Framework nedostupný. Pokud `Global` – klíčové slovo není používáno ve plně kvalifikovaný název. Pro povolení přístupu do daného oboru názvů rozhraní .NET Framework bez použití `Global` – klíčové slovo, můžete zahrnout `Global` – klíčové slovo v `Namespace` příkaz.  
  
 V následujícím příkladu má `Global` – klíčové slovo v `System.Text` deklaraci oboru názvů.  
  
 Pokud `Global` – klíčové slovo nebylo v deklaraci oboru názvů <xref:System.Text.StringBuilder> nelze získat přístup bez zadání `Global.System.Text.StringBuilder`. Pro projekt s názvem `ConsoleApplication1`, odkazuje na `System.Text` by přístup `ConsoleApplication1.System.Text` Pokud `Global` – klíčové slovo nebyl použit.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Postupy: Vytváření a použití sestavení s pomocí příkazového řádku](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Odkazy a příkaz Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Psaní kódu v řešeních pro systém Office](https://msdn.microsoft.com/library/bb608596)
