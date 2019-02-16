---
title: 'Postupy: Simulace událostí myši a klávesnice v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 43641b89ae405caf9807b00b4b3c84f25c4e5e67
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332192"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Postupy: Simulace událostí myši a klávesnice v kódu
Windows Forms poskytuje několik možností pro simulaci programově myši a klávesnice. Toto téma obsahuje přehled těchto možností.  
  
## <a name="simulating-mouse-input"></a>Simulace vstup z myši  
 Nejlepší způsob, jak simulace událostí myši je volání `On` *EventName* metodu, která vyvolává událost myši, kterou chcete simulovat. Tato možnost je obvykle možné pouze v rámci vlastní ovládací prvky a formuláře, protože jsou chráněné metody, které vyvolávají události a nelze přistupovat mimo ovládací prvek nebo formuláře. Například následující kroky ukazují, jak simulovat kliknutím pravým tlačítkem myši v kódu.  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a>Pravým tlačítkem myši na prostřednictvím kódu programu  
  
1.  Vytvoření <xref:System.Windows.Forms.MouseEventArgs> jehož <xref:System.Windows.Forms.MouseEventArgs.Button%2A> je nastavena na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> hodnotu.  
  
2.  Volání <xref:System.Windows.Forms.Control.OnMouseClick%2A> metoda s tímto <xref:System.Windows.Forms.MouseEventArgs> jako argument.  
  
 Další informace o vlastních ovládacích prvcích najdete v tématu [vývoj prvky Windows Forms v době návrhu](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Existují jiné způsoby, jak simulovat vstup z myši. Například prostřednictvím kódu programu nastavit vlastnosti ovládacího prvku, který představuje stav, který se obvykle nastavuje pouze prostřednictvím vstup z myši (například <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost <xref:System.Windows.Forms.CheckBox> ovládací prvek), nebo delegát, který je připojen k této události lze volat přímo můžete Chcete simulovat.  
  
## <a name="simulating-keyboard-input"></a>Simulace vstup z klávesnice  
 I když můžete simulovat vstup z klávesnice s použitím strategie bylo uvedeno výše pro vstup z myši, Windows Forms poskytuje také <xref:System.Windows.Forms.SendKeys> třídu pro odesílání stisknutí kláves do aktivní aplikace.  
  
> [!CAUTION]
>  Pokud vaše aplikace je určena pro mezinárodní širokou škálu klávesnice, použití <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> může vést k nepředvídatelným výsledkům a mělo by se vyhnout.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SendKeys> Třídy byl aktualizován pro rozhraní .NET Framework 3.0 umožňuje jeho použití v aplikacích, které běží na Windows Vista. Zvýšené zabezpečení systému Windows Vista (označované jako řízení uživatelských účtů nebo nástroje Řízení uživatelských účtů) brání předchozích implementacích fungovat podle očekávání.  
>   
>  <xref:System.Windows.Forms.SendKeys> Třídy je náchylný k problémy načasování, což někteří vývojáři měli obejít. Aktualizovanou implementaci přesto náchylné k problémům časování, ale je mírně rychlejší a mohou vyžadovat změny řešení. <xref:System.Windows.Forms.SendKeys> Třídy se pokusí nejprve použít předchozí implementace a pokud se to nepodaří, používá novou implementaci. V důsledku toho <xref:System.Windows.Forms.SendKeys> třída může chovat jinak v různých operačních systémech. Kromě toho, když <xref:System.Windows.Forms.SendKeys> třída používá novou implementaci <xref:System.Windows.Forms.SendKeys.SendWait%2A> metoda nebude čekat zpráv pro zpracování odeslání na jiný proces.  
>   
>  Pokud vaše aplikace závisí na chování konzistentní bez ohledu na operační systém, můžete vynutit <xref:System.Windows.Forms.SendKeys> třídy používat novou implementaci přidáním následujícího nastavení aplikace do souboru app.config.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Chcete-li vynutit <xref:System.Windows.Forms.SendKeys> třídy, které chcete použít předchozí implementaci, použijte hodnotu `"JournalHook"` místo toho.  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a>K odesílání jedním stisknutím tlačítka do stejné aplikace  
  
1.  Volání <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> metodu <xref:System.Windows.Forms.SendKeys> třídy. Aktivní ovládací prvek aplikace bude přijímat zadané stisknutí kláves. Následující příklad kódu používá <xref:System.Windows.Forms.SendKeys.Send%2A> pro simulaci stisknutím klávesy ENTER v situaci, kdy uživatel dvakrát klikne na plochu formuláře. Tento příklad předpokládá <xref:System.Windows.Forms.Form> pomocí jediného <xref:System.Windows.Forms.Button> ovládací prvek, který má pořadové číslo 0.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a>Odeslat stisknutí klávesy na novou aplikaci  
  
1.  Aktivovat okno aplikace, která bude přijímat stisknutí kláves a poté zavolejte <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> metody. Protože neexistuje žádná spravovaná metoda aktivovat jiná aplikace, je nutné použít nativní metody Windows k vynucení fokus na jiné aplikace. Vyvolání platformu používá následující příklad kódu pro volání `FindWindow` a `SetForegroundWindow` metody k aktivaci okno aplikace kalkulačky a poté zavolá <xref:System.Windows.Forms.SendKeys.SendWait%2A> vydat aplikace Kalkulačka řadu výpočty.  
  
    > [!NOTE]
    >  Správné parametry `FindWindow` volání, která vyhledává aplikace Kalkulačka se liší v závislosti na vaší verzi Windows.  Následující kód najde aplikace Kalkulačka na [!INCLUDE[win7](../../../includes/win7-md.md)]. Na [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], změnit první parametr "SciCalc". Spy ++ nástroj, součástí sady Visual Studio, můžete použít k určení správné parametry.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu je hotové aplikace pro předchozí příklady kódu.  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:
- [Uživatelský vstup ve Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
