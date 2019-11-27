---
title: Obory názvů
ms.date: 07/20/2015
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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347333"
---
# <a name="namespaces-in-visual-basic"></a>Obory názvů v jazyce Visual Basic
Obory názvů organizují objekty definované v sestavení. Sestavení mohou obsahovat více oborů názvů, které mohou zase obsahovat jiné obory názvů. Obory názvů zabraňují nejednoznačnosti a zjednodušují odkazy při použití velkých skupin objektů, jako jsou knihovny tříd.  
  
 Například .NET Framework definuje třídu <xref:System.Windows.Forms.ListBox> v oboru názvů <xref:System.Windows.Forms?displayProperty=nameWithType>. Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaného názvu pro tuto třídu:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Zamezení kolizí názvů  
 .NET Framework obory názvů řeší problém, který se někdy nazývá *znečišťování oboru názvů*, ve kterém je vývojář knihovny tříd zabráněno použitím podobných názvů v jiné knihovně. Konflikty se stávajícími součástmi jsou někdy označovány jako *kolize názvů*.  
  
 Například pokud vytvoříte novou třídu s názvem `ListBox`, můžete ji použít uvnitř projektu bez kvalifikace. Pokud však chcete použít třídu .NET Framework <xref:System.Windows.Forms.ListBox> ve stejném projektu, je nutné použít plně kvalifikovaný odkaz, který odkaz nastaví jako jedinečný. Pokud odkaz není jedinečný, Visual Basic vytvoří chybu oznamující, že název je nejednoznačný. Následující příklad kódu ukazuje, jak deklarovat tyto objekty:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Následující ilustrace znázorňuje dvě hierarchie oboru názvů, které obsahují objekt s názvem `ListBox`:  
  
 ![Snímek obrazovky, který ukazuje dvě hierarchie oboru názvů.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Ve výchozím nastavení každý spustitelný soubor, který vytvoříte pomocí Visual Basic, obsahuje obor názvů se stejným názvem jako váš projekt. Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject`, spustitelný soubor ListBoxProject. exe obsahuje obor názvů nazvaný `ListBoxProject`.  
  
 Více sestavení může používat stejný obor názvů. Visual Basic je považuje za jednu sadu názvů. Můžete například definovat třídy pro obor názvů s názvem `SomeNameSpace` v sestavení s názvem `Assemb1`a definovat další třídy pro stejný obor názvů ze sestavení s názvem `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy  
 Plně kvalifikované názvy jsou odkazy na objekty, které jsou s předponou názvu oboru názvů, ve kterém je objekt definován. Můžete použít objekty definované v jiných projektech, pokud vytvoříte odkaz na třídu (kliknutím na **Přidat odkaz** z nabídky **projekt** ) a potom použijete plně kvalifikovaný název objektu v kódu. Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název objektu z jiného oboru názvů projektu:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Plně kvalifikované názvy zabraňují konfliktům názvů, protože umožňují kompilátoru určit, který objekt se používá. Vlastní jména ale můžou být dlouhá a nenáročný. Chcete-li se tomuto problému vyhnout, můžete použít příkaz `Imports` k definování *aliasu*– zkrácený název, který můžete použít místo plně kvalifikovaného názvu. Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a použije tyto aliasy k definování dvou objektů.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Použijete-li příkaz `Imports` bez aliasu, můžete použít všechny názvy v tomto oboru názvů bez kvalifikace, pokud jsou pro projekt jedinečné. Pokud váš projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, je nutné plně kvalifikovat tento název při použití. Předpokládejme například, že váš projekt obsahuje následující dva `Imports` příkazy:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Pokud se pokusíte použít `Class1` bez úplného zařazení, Visual Basic vytvoří chybu s oznámením, že název `Class1` je dvojznačný.  
  
## <a name="namespace-level-statements"></a>Příkazy na úrovni oboru názvů  
 V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegáty, výčty, struktury a jiné obory názvů. Na úrovni oboru názvů nelze definovat položky, jako jsou vlastnosti, procedury, proměnné a události. Tyto položky musí být deklarovány v rámci kontejnerů, jako jsou moduly, struktury nebo třídy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Klíčové slovo Global v plně kvalifikovaném názvu  
 Pokud jste definovali vnořenou hierarchii oborů názvů, kód uvnitř této hierarchie může být zablokován pro přístup k oboru názvů <xref:System?displayProperty=nameWithType> .NET Framework. Následující příklad znázorňuje hierarchii, ve které `SpecialSpace.System` obor názvů blokuje přístup k <xref:System?displayProperty=nameWithType>.  
  
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
  
 V důsledku toho kompilátor Visual Basic nemůže úspěšně přeložit odkaz na <xref:System.Int32?displayProperty=nameWithType>, protože `SpecialSpace.System` nedefinuje `Int32`. Pomocí klíčového slova `Global` můžete spustit řetěz kvalifikace na krajní úrovni .NET Framework knihovny tříd. To umožňuje zadat obor názvů <xref:System?displayProperty=nameWithType> nebo jakýkoli jiný obor názvů v knihovně tříd. Toto dokládá následující příklad.  
  
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
  
 `Global` můžete použít pro přístup k dalším oborům názvů na kořenové úrovni, jako je například <xref:Microsoft.VisualBasic?displayProperty=nameWithType>, a jakémukoli oboru názvů přidruženému k vašemu projektu.  
  
## <a name="global-keyword-in-namespace-statements"></a>Klíčové slovo Global v příkazech Namespace  
 Můžete také použít klíčové slovo `Global` v [příkazu Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). To umožňuje definovat obor názvů mimo kořenový obor názvů vašeho projektu.  
  
 Všechny obory názvů v projektu jsou založené na kořenovém oboru názvů projektu.  Visual Studio přiřadí název vašeho projektu jako výchozí kořenový obor názvů pro veškerý kód v projektu. Například pokud je projekt pojmenován `ConsoleApplication1`, jeho programovací prvky patří do oboru názvů `ConsoleApplication1`. Pokud deklarujete `Namespace Magnetosphere`, odkazy na `Magnetosphere` v projektu budou přistupovat `ConsoleApplication1.Magnetosphere`.  
  
 Následující příklady používají klíčové slovo `Global` k deklaraci oboru názvů mimo kořenový obor názvů pro projekt.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 V deklaraci oboru názvů nelze `Global` vnořovat do jiného oboru názvů.  
  
 Můžete použít [stránku aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) k zobrazení a úpravě **kořenového oboru názvů** projektu.  Pro nové projekty je výchozím **kořenovým oborem názvů** název projektu. Chcete-li `Global` být oborem názvů nejvyšší úrovně, můžete vymazat položku **kořenového oboru názvů** tak, aby bylo pole prázdné. Vymazání **kořenového oboru názvů** odebere potřebu klíčového slova `Global` v deklaracích oboru názvů.  
  
 Pokud příkaz `Namespace` deklaruje název, který je také obor názvů v .NET Framework, .NET Framework obor názvů bude k dispozici, pokud klíčové slovo `Global` není použito v plně kvalifikovaném názvu. Chcete-li povolit přístup k tomuto oboru názvů .NET Framework bez použití klíčového slova `Global`, můžete do příkazu `Namespace` zahrnout klíčové slovo `Global`.  
  
 V následujícím příkladu je klíčové slovo `Global` v deklaraci oboru názvů `System.Text`.  
  
 Pokud klíčové slovo `Global` nebylo v deklaraci oboru názvů přítomno, <xref:System.Text.StringBuilder> nelze přistupovat bez zadání `Global.System.Text.StringBuilder`. V případě projektu s názvem `ConsoleApplication1`má odkaz na `System.Text` přístup `ConsoleApplication1.System.Text`, pokud nebylo použito klíčové slovo `Global`.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Odkazy a příkaz Imports](references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Psaní kódu v řešeních pro systém Office](/visualstudio/vsto/writing-code-in-office-solutions)
