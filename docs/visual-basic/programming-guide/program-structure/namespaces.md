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
ms.openlocfilehash: 087c6f02e1fca9cf2664ca76581c08a9b1a5e447
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398354"
---
# <a name="namespaces-in-visual-basic"></a>Obory názvů v jazyce Visual Basic
Obory názvů organizují objekty definované v sestavení. Sestavení mohou obsahovat více oborů názvů, které mohou zase obsahovat jiné obory názvů. Obory názvů zabraňují nejednoznačnosti a zjednodušují odkazy při použití velkých skupin objektů, jako jsou knihovny tříd.  
  
 Například .NET Framework definuje <xref:System.Windows.Forms.ListBox> třídu v <xref:System.Windows.Forms?displayProperty=nameWithType> oboru názvů. Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaného názvu pro tuto třídu:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Zamezení kolizí názvů  
 .NET Framework obory názvů řeší problém, který se někdy nazývá *znečišťování oboru názvů*, ve kterém je vývojář knihovny tříd zabráněno použitím podobných názvů v jiné knihovně. Konflikty se stávajícími součástmi jsou někdy označovány jako *kolize názvů*.  
  
 Například pokud vytvoříte novou třídu s názvem `ListBox` , můžete ji použít uvnitř projektu bez kvalifikace. Pokud však chcete použít <xref:System.Windows.Forms.ListBox> třídu .NET Framework ve stejném projektu, je nutné použít plně kvalifikovaný odkaz pro odkazování na jedinečný. Pokud odkaz není jedinečný, Visual Basic vytvoří chybu oznamující, že název je nejednoznačný. Následující příklad kódu ukazuje, jak deklarovat tyto objekty:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Následující ilustrace znázorňuje dvě hierarchie oboru názvů, které obsahují objekt s názvem `ListBox` :  
  
 ![Snímek obrazovky, který ukazuje dvě hierarchie oboru názvů.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Ve výchozím nastavení každý spustitelný soubor, který vytvoříte pomocí Visual Basic, obsahuje obor názvů se stejným názvem jako váš projekt. Například pokud definujete objekt v rámci projektu s názvem `ListBoxProject` , spustitelný soubor ListBoxProject. exe obsahuje obor názvů s názvem `ListBoxProject` .  
  
 Více sestavení může používat stejný obor názvů. Visual Basic je považuje za jednu sadu názvů. Můžete například definovat třídy pro obor názvů nazvaný `SomeNameSpace` v sestavení s názvem `Assemb1` a definovat další třídy pro stejný obor názvů ze sestavení s názvem `Assemb2` .  
  
## <a name="fully-qualified-names"></a>Plně kvalifikované názvy  
 Plně kvalifikované názvy jsou odkazy na objekty, které jsou s předponou názvu oboru názvů, ve kterém je objekt definován. Můžete použít objekty definované v jiných projektech, pokud vytvoříte odkaz na třídu (kliknutím na **Přidat odkaz** z nabídky **projekt** ) a potom použijete plně kvalifikovaný název objektu v kódu. Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název objektu z jiného oboru názvů projektu:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Plně kvalifikované názvy zabraňují konfliktům názvů, protože umožňují kompilátoru určit, který objekt se používá. Vlastní jména ale můžou být dlouhá a nenáročný. Chcete-li se tomuto problému vyhnout, můžete použít `Imports` příkaz k definování *aliasu*– zkrácený název, který můžete použít místo plně kvalifikovaného názvu. Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a použije tyto aliasy k definování dvou objektů.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Použijete-li `Imports` příkaz bez aliasu, můžete použít všechny názvy v tomto oboru názvů bez kvalifikace, pokud jsou pro projekt jedinečné. Pokud váš projekt obsahuje `Imports` příkazy pro obory názvů, které obsahují položky se stejným názvem, je nutné plně kvalifikovat tento název při použití. Předpokládejme například, že váš projekt obsahuje následující dva `Imports` příkazy:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Pokud se pokusíte použít `Class1` bez plně kvalifikovaného názvu, Visual Basic vytvoří chybu s oznámením, že název `Class1` je nejednoznačný.  
  
## <a name="namespace-level-statements"></a>Příkazy na úrovni oboru názvů  
 V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegáty, výčty, struktury a jiné obory názvů. Na úrovni oboru názvů nelze definovat položky, jako jsou vlastnosti, procedury, proměnné a události. Tyto položky musí být deklarovány v rámci kontejnerů, jako jsou moduly, struktury nebo třídy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Klíčové slovo Global v plně kvalifikovaném názvu  
 Pokud jste definovali vnořenou hierarchii oborů názvů, kód uvnitř této hierarchie může být zablokován pro přístup k <xref:System?displayProperty=nameWithType> oboru názvů .NET Framework. Následující příklad znázorňuje hierarchii, ve které `SpecialSpace.System` obor názvů blokuje přístup <xref:System?displayProperty=nameWithType> .  
  
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
  
 V důsledku toho kompilátor Visual Basic nemůže úspěšně přeložit odkaz na <xref:System.Int32?displayProperty=nameWithType> , protože `SpecialSpace.System` nedefinuje `Int32` . Klíčové slovo lze použít `Global` ke spuštění řetězu kvalifikace na nejvzdálenější úrovni knihovny tříd .NET Framework. To umožňuje zadat <xref:System?displayProperty=nameWithType> obor názvů nebo jakýkoli jiný obor názvů v knihovně tříd. Toto dokládá následující příklad.  
  
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
  
 Můžete použít `Global` pro přístup k dalším oborům názvů na kořenové úrovni, jako <xref:Microsoft.VisualBasic?displayProperty=nameWithType> je a jakýkoli obor názvů přidružený k vašemu projektu.  
  
## <a name="global-keyword-in-namespace-statements"></a>Klíčové slovo Global v příkazech Namespace  
 Klíčové slovo lze použít také `Global` v [příkazu Namespace](../../language-reference/statements/namespace-statement.md). To umožňuje definovat obor názvů mimo kořenový obor názvů vašeho projektu.  
  
 Všechny obory názvů v projektu jsou založené na kořenovém oboru názvů projektu.  Visual Studio přiřadí název vašeho projektu jako výchozí kořenový obor názvů pro veškerý kód v projektu. Například pokud je váš projekt pojmenován `ConsoleApplication1` , jeho programovací prvky patří do oboru názvů `ConsoleApplication1` . Pokud deklarujete `Namespace Magnetosphere` , odkazy na `Magnetosphere` v projektu budou mít přístup `ConsoleApplication1.Magnetosphere` .  
  
 Následující příklady používají `Global` klíčové slovo k deklaraci oboru názvů mimo kořenový obor názvů pro projekt.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 V deklaraci oboru názvů `Global` nelze vnořovat do jiného oboru názvů.  
  
 Můžete použít [stránku aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) k zobrazení a úpravě **kořenového oboru názvů** projektu.  Pro nové projekty je výchozím **kořenovým oborem názvů** název projektu. Chcete-li `Global` být příčinou oboru názvů nejvyšší úrovně, můžete vymazat položku **kořenového oboru názvů** tak, aby bylo pole prázdné. Vymazání **kořenového oboru názvů** odebere potřebu `Global` klíčového slova v deklaracích oboru názvů.  
  
 Pokud `Namespace` příkaz deklaruje název, který je také obor názvů v .NET Framework, .NET Framework obor názvů nebude k dispozici, pokud `Global` klíčové slovo není použito v plně kvalifikovaném názvu. Chcete-li povolit přístup k tomuto oboru názvů .NET Framework bez použití `Global` klíčového slova, můžete `Global` do příkazu zahrnout klíčové slovo `Namespace` .  
  
 V následujícím příkladu je `Global` klíčové slovo v `System.Text` deklaraci oboru názvů.  
  
 Pokud `Global` klíčové slovo nebylo přítomno v deklaraci oboru názvů, <xref:System.Text.StringBuilder> nelze k němu přistupovat bez zadání `Global.System.Text.StringBuilder` . V případě projektu s názvem `ConsoleApplication1` mají odkazy na `System.Text` přístup, `ConsoleApplication1.System.Text` Pokud `Global` klíčové slovo nebylo použito.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Odkazy a příkaz Imports](references-and-the-imports-statement.md)
- [Imports – příkaz (obor názvů a typ rozhraní .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Psaní kódu v řešeních pro systém Office](/visualstudio/vsto/writing-code-in-office-solutions)
