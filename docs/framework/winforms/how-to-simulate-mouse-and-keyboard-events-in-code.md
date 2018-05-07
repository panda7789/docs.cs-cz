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
ms.openlocfilehash: cdb37fe549ebfbcdb5a0c5b6008a1922fdbf471b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Postupy: Simulace událostí myši a klávesnice v kódu
Windows Forms poskytuje několik možností pro simulaci prostřednictvím kódu programu myši a vstup z klávesnice. Toto téma obsahuje přehled těchto možností.  
  
## <a name="simulating-mouse-input"></a>Simulaci vstup myši  
 Nejlepší způsob, jak simulace událostí myši je volat `On` *EventName* metoda, která se vyvolá událost, myš, kterou chcete simulovat. Tuto možnost obvykle je možné pouze v rámci vlastní ovládací prvky a formulářů, protože metody, které vyvolávání událostí jsou chráněné a nelze přistupovat mimo ovládacího prvku nebo formuláře. Například následující kroky ukazují, jak k simulaci, kliknete pravým tlačítkem myši v kódu.  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a>Prostřednictvím kódu programu kliknout pravým tlačítkem myši  
  
1.  Vytvoření <xref:System.Windows.Forms.MouseEventArgs> jejichž <xref:System.Windows.Forms.MouseEventArgs.Button%2A> je nastavena na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> hodnotu.  
  
2.  Volání <xref:System.Windows.Forms.Control.OnMouseClick%2A> metoda pomocí této <xref:System.Windows.Forms.MouseEventArgs> jako argument.  
  
 Další informace o vlastních ovládacích prvcích najdete v tématu [vývoj ovládacích prvků Windows Forms v době návrhu](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Pro simulaci vstup z myši i jinými způsoby. Například můžete programově nastavit řízení vlastnost, která představuje stav, který se obvykle nastavuje prostřednictvím vstup z myši (například <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost <xref:System.Windows.Forms.CheckBox> ovládací prvek), nebo přímo volat delegáta, který je připojen k události je Chcete simulovat.  
  
## <a name="simulating-keyboard-input"></a>Simulaci vstup z klávesnice  
 I když můžete simulovat vstup z klávesnice s použitím strategie výše popsané pro vstup z myši, Windows Forms poskytuje taky <xref:System.Windows.Forms.SendKeys> třídu pro odesílání stisknutí kláves aplikace aktivní.  
  
> [!CAUTION]
>  Pokud vaše aplikace je určená pro mezinárodní s různými klávesnice, použití <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> může vést k neočekávaným výsledkům yield a je nutno.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SendKeys> Třída byla aktualizována pro rozhraní .NET Framework 3.0, aby jeho použití v aplikacích, které běží na systému Windows Vista. Rozšířené zabezpečení systému Windows Vista (označované jako řízení uživatelských účtů nebo nástroje Řízení uživatelských účtů) zabraňuje předchozí implementace z pracovní podle očekávání.  
>   
>  <xref:System.Windows.Forms.SendKeys> Třída je ohrožena útoky založenými na problémy načasování, kterým byly někteří vývojáři obejít. Aktualizované implementace přesto náchylné k problémy načasování, ale je mírně rychlejší a může vyžadovat změny řešení. <xref:System.Windows.Forms.SendKeys> Třídy pokusí nejdříve použít předchozí implementace a pokud to nepomůže, používá novou implementací. V důsledku toho <xref:System.Windows.Forms.SendKeys> třída může chovat jinak v různých operačních systémech. Kromě toho, když <xref:System.Windows.Forms.SendKeys> třída používá nové implementace <xref:System.Windows.Forms.SendKeys.SendWait%2A> metoda nebude čekat na zprávy, které mají být zpracovány odeslání na jiný proces.  
>   
>  Pokud vaše aplikace závisí na konzistentní chování bez ohledu na operační systém, můžete vynutit <xref:System.Windows.Forms.SendKeys> třídu se má použít novou implementací přidáním následující nastavení aplikace do souboru app.config.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Chcete-li vynutit <xref:System.Windows.Forms.SendKeys> třídy, které chcete použít předchozí implementace, použijte hodnotu `"JournalHook"` místo.  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a>K odeslání stisknutí klávesy stejná aplikace  
  
1.  Volání <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> metodu <xref:System.Windows.Forms.SendKeys> třídy. Zadaný stisknutí kláves dostane aktivní ovládací prvek aplikace. Následující příklad kódu používá <xref:System.Windows.Forms.SendKeys.Send%2A> k simulaci při poklepání prostor ve tvaru, stisknete klávesu ENTER. Tento příklad předpokládá <xref:System.Windows.Forms.Form> s jedním <xref:System.Windows.Forms.Button> ovládací prvek, který má pořadové číslo 0.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a>K odeslání stisknutí klávesy jinou aplikaci  
  
1.  Aktivovat okna aplikace, která bude přijímat stisknutí kláves a potom zavolejte <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> metoda. Protože neexistuje žádná metoda spravované aktivovat jiná aplikace, je nutné použít nativní metody Windows vynutit fokus na jiné aplikace. Vyvolání platformou používá následující příklad kódu pro volání `FindWindow` a `SetForegroundWindow` metody aktivace okna aplikace kalkulačky a poté zavolá <xref:System.Windows.Forms.SendKeys.SendWait%2A> vystavit řadu Výpočty kalkulačky aplikace.  
  
    > [!NOTE]
    >  Správné parametry `FindWindow` volání, která vyhledává aplikace Kalkulačka lišit v závislosti na vaší verzi systému Windows.  Následující kód vyhledá aplikace Kalkulačka v [!INCLUDE[win7](../../../includes/win7-md.md)]. Na [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], změňte první parametr "SciCalc". Nástroje Spy ++ nástroj, zahrnutá v sadě Visual Studio, můžete určit správné parametry.  
  
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
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 [Uživatelský vstup ve Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)
