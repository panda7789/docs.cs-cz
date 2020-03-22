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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400671"
---
# <a name="namespaces-in-visual-basic"></a>Obory názvů v jazyce Visual Basic
Obory názvů uspořádají objekty definované v sestavení. Sestavení mohou obsahovat více oborů názvů, které mohou zase obsahovat další obory názvů. Obory názvů zabraňují nejednoznačnosti a zjednodušují odkazy při použití velkých skupin objektů, jako jsou knihovny tříd.  
  
 Například rozhraní .NET Framework <xref:System.Windows.Forms.ListBox> definuje třídu v oboru <xref:System.Windows.Forms?displayProperty=nameWithType> názvů. Následující fragment kódu ukazuje, jak deklarovat proměnnou pomocí plně kvalifikovaného názvu pro tuto třídu:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Předcházení kolizím názvů  
 Obory názvů rozhraní .NET Framework řeší problém, který se někdy nazývá *znečištění oboru názvů*, ve kterém je vývojáři knihovny tříd bráněno použitím podobných názvů v jiné knihovně. Tyto konflikty s existujícími součástmi se někdy nazývají *kolize názvů*.  
  
 Pokud například vytvoříte novou `ListBox`třídu s názvem , můžete ji použít v rámci projektu bez kvalifikace. Pokud však chcete použít třídu <xref:System.Windows.Forms.ListBox> rozhraní .NET Framework ve stejném projektu, musíte použít plně kvalifikovaný odkaz, aby byl odkaz jedinečný. Pokud odkaz není jedinečný, visual basic vytvoří chybu oznamující, že název je nejednoznačný. Následující příklad kódu ukazuje, jak deklarovat tyto objekty:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 Následující obrázek znázorňuje dvě hierarchie oboru `ListBox`názvů, obě obsahující objekt s názvem :  
  
 ![Snímek obrazovky, který zobrazuje dvě hierarchie oboru názvů.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Ve výchozím nastavení obsahuje každý spustitelný soubor, který vytvoříte pomocí jazyka Visual Basic, obor názvů se stejným názvem jako projekt. Pokud například definujete objekt v `ListBoxProject`rámci projektu s názvem , obsahuje spustitelný soubor `ListBoxProject`ListBoxProject.exe název obor názvů s názvem .  
  
 Více sestavení můžete použít stejný obor názvů. Visual Basic s nimi zachází jako s jednou sadou názvů. Můžete například definovat třídy pro `SomeNameSpace` obor názvů `Assemb1`volaný v sestavení s názvem a `Assemb2`definovat další třídy pro stejný obor názvů z sestavení s názvem .  
  
## <a name="fully-qualified-names"></a>Plně kvalifikovaná jména  
 Plně kvalifikované názvy jsou odkazy na objekty, které jsou předponou s názvem oboru názvů, ve kterém je objekt definován. Objekty definované v jiných projektech můžete použít, pokud vytvoříte odkaz na třídu (výběrem **možnosti Přidat odkaz** z nabídky **Projekt)** a potom použijete plně kvalifikovaný název objektu v kódu. Následující fragment kódu ukazuje, jak použít plně kvalifikovaný název pro objekt z oboru názvů jiného projektu:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Plně kvalifikované názvy zabránit konfliktům názvů, protože umožňují kompilátoru určit, který objekt se používá. Nicméně, jména samotná mohou být dlouhá a těžkopádná. Chcete-li tento problém obejít, můžete pomocí příkazu `Imports` definovat *alias*– zkrácený název, který můžete použít místo plně kvalifikovaného názvu. Například následující příklad kódu vytvoří aliasy pro dva plně kvalifikované názvy a používá tyto aliasy k definování dvou objektů.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Pokud použijete `Imports` příkaz bez aliasu, můžete použít všechny názvy v tomto oboru názvů bez kvalifikace za předpokladu, že jsou jedinečné pro projekt. Pokud váš `Imports` projekt obsahuje příkazy pro obory názvů, které obsahují položky se stejným názvem, je nutné plně kvalifikovat tento název při jeho použití. Předpokládejme například, že projekt obsahuje `Imports` následující dva příkazy:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Pokud se pokusíte použít `Class1` bez úplného zařazení, Visual Basic `Class1` vytvoří chybu oznamující, že název je nejednoznačný.  
  
## <a name="namespace-level-statements"></a>Příkazy úrovně oboru názvů  
 V rámci oboru názvů můžete definovat položky, jako jsou moduly, rozhraní, třídy, delegáty, výčty, struktury a další obory názvů. Nelze definovat položky, jako jsou vlastnosti, procedury, proměnné a události na úrovni oboru názvů. Tyto položky musí být deklarovány v rámci kontejnerů, jako jsou moduly, struktury nebo třídy.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Globální klíčové slovo v plně kvalifikovaných názvech  
 Pokud jste definovali vnořenou hierarchii oborů názvů, může <xref:System?displayProperty=nameWithType> být kód uvnitř této hierarchie blokován v přístupu k oboru názvů rozhraní .NET Framework. Následující příklad ilustruje hierarchii, `SpecialSpace.System` ve které obor <xref:System?displayProperty=nameWithType>názvů blokuje přístup k aplikaci .  
  
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
  
 V důsledku toho kompilátor jazyka visual basic <xref:System.Int32?displayProperty=nameWithType>nemůže `SpecialSpace.System` úspěšně přeložit `Int32`odkaz na , protože nedefinuje . `Global` Klíčové slovo můžete použít ke spuštění řetězce kvalifikace na nejkrajnější úrovni knihovny tříd rozhraní .NET Framework. To umožňuje zadat <xref:System?displayProperty=nameWithType> obor názvů nebo jiný obor názvů v knihovně tříd. Toto dokládá následující příklad.  
  
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
  
 Můžete použít `Global` pro přístup k jiným oborům <xref:Microsoft.VisualBasic?displayProperty=nameWithType>názvů kořenové úrovně, jako je například aplikace , a ke všem oborům názvů přidruženým k projektu.  
  
## <a name="global-keyword-in-namespace-statements"></a>Globální klíčové slovo v příkazech oboru názvů  
 Klíčové `Global` slovo můžete také použít v [prohlášení oboru názvů](../../../visual-basic/language-reference/statements/namespace-statement.md). To umožňuje definovat obor názvů z kořenového oboru názvů projektu.  
  
 Všechny obory názvů v projektu jsou založeny na kořenovém oboru názvů pro projekt.  Visual Studio přiřadí název projektu jako výchozí kořenový obor názvů pro veškerý kód v projektu. Pokud je například projekt `ConsoleApplication1`pojmenován , jeho programovací prvky patří do oboru názvů `ConsoleApplication1`. Pokud deklarujete `Namespace Magnetosphere`, odkazy `Magnetosphere` v projektu budou mít přístup `ConsoleApplication1.Magnetosphere`.  
  
 Následující příklady používají `Global` klíčové slovo k deklarování oboru názvů mimo kořenový obor názvů pro projekt.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 V deklaraci `Global` oboru názvů nelze vnořit do jiného oboru názvů.  
  
 Můžete použít [stránku aplikace, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) k zobrazení a úpravě **kořenového oboru názvů** projektu.  U nových projektů je výchozí výchozí **obor kořenového názvového serveru** název projektu. Chcete-li způsobit, `Global` že se jedná o obor názvů nejvyšší úrovně, můžete vymazat položku **Kořenového oboru názvů,** aby bylo pole prázdné. **Vymazáním kořenového oboru** názvů `Global` odeberete potřebu klíčového slova v deklaracích oboru názvů.  
  
 Pokud `Namespace` příkaz deklaruje název, který je také obor názvů v rozhraní .NET `Global` Framework, obor názvů rozhraní .NET Framework přestane být k dispozici, pokud klíčové slovo není použito v plně kvalifikovaném názvu. Chcete-li povolit přístup k tomuto `Global` oboru názvů rozhraní `Global` .NET `Namespace` Framework bez použití klíčového slova, můžete klíčové slovo zahrnout do příkazu.  
  
 Následující příklad má `Global` klíčové `System.Text` slovo v deklaraci oboru názvů.  
  
 Pokud `Global` klíčové slovo nebylo přítomno v <xref:System.Text.StringBuilder> deklaraci oboru názvů, `Global.System.Text.StringBuilder`nebylo možné získat přístup bez zadání . Pro projekt `ConsoleApplication1`s názvem `System.Text` , `ConsoleApplication1.System.Text` odkazy `Global` na přístup, pokud klíčové slovo nebylo použito.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Odkazy a příkaz Imports](references-and-the-imports-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Psaní kódu v řešeních pro systém Office](/visualstudio/vsto/writing-code-in-office-solutions)
