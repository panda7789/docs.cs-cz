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
ms.openlocfilehash: 52f89df8d7f28f0e00c3becd9005b46e52b5532c
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960202"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Postupy: Simulace událostí myši a klávesnice v kódu

Model Windows Forms poskytuje několik možností pro programové simulaci vstupu myši a klávesnice. Toto téma poskytuje přehled těchto možností.

## <a name="simulating-mouse-input"></a>Simulace vstupu myši

Nejlepším způsobem, jak simulovat události myši, je zavolat metodu `On`*EventName* , která vyvolává událost myši, kterou chcete simulovat. Tato možnost je obvykle k dispozici pouze v rámci vlastních ovládacích prvků a formulářů, protože metody, které vyvolávají události, jsou chráněny a nelze je používat mimo ovládací prvek nebo formulář. Následující kroky například ukazují, jak simulovat kliknutí pravým tlačítkem myši v kódu.

#### <a name="to-programmatically-click-the-right-mouse-button"></a>Postup při programovém kliknutí pravým tlačítkem myši

1. Vytvořte <xref:System.Windows.Forms.MouseEventArgs>, jehož vlastnost <xref:System.Windows.Forms.MouseEventArgs.Button%2A> je nastavena na hodnotu <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType>.

2. Jako argument volejte metodu <xref:System.Windows.Forms.Control.OnMouseClick%2A> s tímto <xref:System.Windows.Forms.MouseEventArgs>.

Další informace o vlastních ovládacích prvcích najdete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](./controls/developing-windows-forms-controls-at-design-time.md).

Existují i jiné způsoby, jak simulovat vstup z myši. Můžete například programově nastavit vlastnost ovládacího prvku, která představuje stav, který je obvykle nastaven prostřednictvím vstupu myši (například vlastnost <xref:System.Windows.Forms.CheckBox.Checked%2A> ovládacího prvku <xref:System.Windows.Forms.CheckBox>), nebo můžete přímo volat delegáta, který je připojen k události, kterou chcete simulovat.

## <a name="simulating-keyboard-input"></a>Simulace vstupu z klávesnice

I když můžete simulovat vstup z klávesnice pomocí výše popsaných strategií pro vstup myši, model Windows Forms taky poskytuje <xref:System.Windows.Forms.SendKeys>ou třídu pro posílání klávesových úhozů do aktivní aplikace.

> [!CAUTION]
> Pokud je vaše aplikace určena pro mezinárodní použití s celou řadou klávesnic, použití <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> může přinést nepředvídatelné výsledky a je třeba se jim vyhnout.

> [!NOTE]
> <xref:System.Windows.Forms.SendKeys> třída byla aktualizována pro .NET Framework 3,0, aby ji bylo možné použít v aplikacích, které jsou spuštěny v systému Windows Vista. Vyšší zabezpečení systému Windows Vista (označované jako řízení uživatelských účtů nebo UAC) brání předchozí implementaci v práci podle očekávání.
>
> Třída <xref:System.Windows.Forms.SendKeys> je náchylná k časování problémů, které někteří vývojáři museli obejít. Aktualizovaná implementace je stále náchylná k problémům časování, ale je mírně rychlejší a může vyžadovat změny v alternativním řešení. Třída <xref:System.Windows.Forms.SendKeys> se pokusí použít nejprve předchozí implementaci a v případě, že dojde k chybě, použije novou implementaci. V důsledku toho se třída <xref:System.Windows.Forms.SendKeys> může chovat odlišně v různých operačních systémech. Kromě toho, pokud <xref:System.Windows.Forms.SendKeys> třída používá novou implementaci, metoda <xref:System.Windows.Forms.SendKeys.SendWait%2A> nečeká na zpracování zpráv při jejich odeslání do jiného procesu.
>
> Pokud vaše aplikace spoléhá na konzistentní chování bez ohledu na operační systém, můžete vynutit, aby třída <xref:System.Windows.Forms.SendKeys> používala novou implementaci přidáním následujícího nastavení aplikace do souboru App. config.
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> Chcete-li vynutit, aby třída <xref:System.Windows.Forms.SendKeys> používala předchozí implementaci, použijte místo toho hodnotu `"JournalHook"`.

#### <a name="to-send-a-keystroke-to-the-same-application"></a>Odeslání stisknutí klávesy ke stejné aplikaci

1. Zavolejte metodu <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> třídy <xref:System.Windows.Forms.SendKeys>. Zadané úhozy kláves budou přijímány aktivním ovládacím prvkem aplikace. Následující příklad kódu používá <xref:System.Windows.Forms.SendKeys.Send%2A> pro simulaci stisknutí klávesy ENTER, když uživatel dvakrát klikne na povrch formuláře. Tento příklad předpokládá <xref:System.Windows.Forms.Form> s jedním <xref:System.Windows.Forms.Button> ovládacím prvkem, který má index karty 0.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>Odeslání úhozu do jiné aplikace

1. Aktivujte okno aplikace, které bude přijímat stisknutí kláves, a potom zavolejte metodu <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A>. Vzhledem k tomu, že neexistuje žádná spravovaná metoda pro aktivaci jiné aplikace, je nutné použít nativní metody systému Windows k vynucení fokusu na jiné aplikace. Následující příklad kódu používá vyvolání platformy pro volání metod `FindWindow` a `SetForegroundWindow` k aktivaci okna aplikace kalkulačky a následné volání <xref:System.Windows.Forms.SendKeys.SendWait%2A> pro vydání řady výpočtů do aplikace kalkulačky.

    > [!NOTE]
    > Správné parametry `FindWindow` volání, které vyhledává aplikaci kalkulačky, se liší v závislosti na vaší verzi systému Windows.  Následující kód vyhledá aplikaci kalkulačky ve Windows 7. V systému Windows Vista změňte první parametr na "SciCalc". K určení správných parametrů můžete použít nástroj Spy + +, který je součástí sady Visual Studio.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>Příklad

Následující příklad kódu je kompletní aplikace pro předchozí příklady kódu.

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento příklad vyžaduje:

- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.

## <a name="see-also"></a>Viz také:

- [Uživatelský vstup ve Windows Forms](user-input-in-windows-forms.md)
