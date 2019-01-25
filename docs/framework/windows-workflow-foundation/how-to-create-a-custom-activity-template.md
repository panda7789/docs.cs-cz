---
title: 'Postupy: Vytvoření vlastní šablony aktivity'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: c90721676fc5b77704ee86bcd5e98c99e3af6683
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512707"
---
# <a name="how-to-create-a-custom-activity-template"></a>Postupy: Vytvoření vlastní šablony aktivity

Vlastní aktivita šablony slouží k přizpůsobení konfigurace aktivit, včetně vlastních složených aktivit, tak, aby uživatelé nebudou mít k vytvoření každé aktivity jednotlivě a nakonfigurovat jejich vlastnosti a další nastavení ručně. Tyto vlastní šablony může být k dispozici v **nástrojů** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] nebo v návrháři se změněným hostováním, ze kterého uživatelé můžete přetáhnout na předem návrhovou plochu. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dodává se sadou dobrým příkladem takové šablony: [návrhář šablony SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [návrhář šablony ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v [návrháři aktivit zasílání zpráv](/visualstudio/workflow-designer/messaging-activity-designers) kategorie.

 První postup v tomto tématu popisuje, jak vytvořit vlastní šablony aktivity pro **zpoždění** aktivity a druhý postup popisuje stručně ho zpřístupní v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] k ověření, zda funguje vlastní šablonu.

 Vlastní aktivita šablony musí implementovat <xref:System.Activities.Presentation.IActivityTemplateFactory>. Rozhraní má jediný <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, pomocí kterého můžete vytvořit a nakonfigurovat instance aktivit použít v šabloně.

## <a name="to-create-a-template-for-the-delay-activity"></a>Vytvoření šablony aktivity Delay

1.  Start Visual Studio 2010.

2.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

3.  V **typy projektů** vyberte **pracovního postupu** buď z **Visual C#** projekty nebo **jazyka Visual Basic** seskupení v závislosti na vaší preferovaný jazyk.

4.  V **šablony** vyberte **knihovny aktivit**.

5.  V **název** zadejte `DelayActivityTemplate`.

6.  Přijměte výchozí hodnoty v **umístění** a **název řešení** textová pole a pak klikněte na tlačítko **OK**.

7.  Klikněte pravým tlačítkem na adresář odkazy projektu DelayActivityTemplate v **Průzkumníka řešení** a zvolte **přidat odkaz** otevřít **přidat odkaz** dialogové okno.

8.  Přejděte na **.NET** kartě a vyberte **PresentationFramework** z **název komponenty** sloupce na levé straně a klikněte na **OK** přidat odkaz do souboru knihovně PresentationFramework.dll.

9. Opakujte tento postup pro přidání odkazů System.Activities.Presentation.dll a knihovně WindowsBase.dll soubory.

10. Klikněte pravým tlačítkem na projekt DelayActivityTemplate v **Průzkumníka řešení** a zvolte **přidat** a potom **nová položka** otevřít **přidat novou položku**dialogové okno.

11. Vyberte **třídy** šablony, pojmenujte ho MyDelayTemplate a potom klikněte na **OK**.

12. Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.

    ```
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Implementace <xref:System.Activities.Presentation.IActivityTemplateFactory> s `MyDelayActivity` třídy následujícím kódem. Tím se nakonfiguruje zpoždění Doba trvání 10 sekund.

    ```
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. Vyberte **sestavit řešení** z **sestavení** nabídky ke generování souboru DelayActivityTemplate.dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Chcete-li šablonu zpřístupnit v Návrháři pracovních postupů

1.  Klikněte pravým tlačítkem na řešení DelayActivityTemplate v **Průzkumníka řešení** a zvolte **přidat** a potom **nový projekt** otevřít **přidat nový projekt** dialogové okno.

2.  Vyberte **Konzolová aplikace pracovního postupu** šablony, pojmenujte ho `CustomActivityTemplateApp`a potom klikněte na tlačítko **OK**.

3.  Klikněte pravým tlačítkem na adresář odkazy projektu CustomActivityTemplateApp v **Průzkumníka řešení** a zvolte **přidat odkaz** otevřít **přidat odkaz** dialogového okna pole.

4.  Přejděte na **projekty** kartě a vyberte **DelayActivityTemplate** z **název projektu** sloupce na levé straně a klikněte na **OK** přidáte odkaz na soubor DelayActivityTemplate.dll, který jste vytvořili v prvním postupu.

5.  Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp v **Průzkumníka řešení** a zvolte **sestavení** pro kompilaci aplikace.

6.  Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp v **Průzkumníka řešení** a zvolte **nastavit jako spouštěný projekt**.

7.  Vyberte **spustit bez ladění** z **ladění** nabídky a stisknutím libovolné klávesy pokračovat po zobrazení výzvy v okně cmd.exe.

8.  Otevřete soubor Workflow1.xaml a otevřít **nástrojů**.

9. Vyhledejte **MyDelayActivity** šablony **DelayActivityTemplate** kategorie. Přetáhněte jej na návrhovou plochu. Potvrďte v **vlastnosti** okna, která `Duration` vlastnost byla nastavena na 10 sekund.

## <a name="example"></a>Příklad
 Soubor MyDelayActivity.cs by měl obsahovat následující kód.

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [Přizpůsobení prostředí pro návrh pracovního postupu](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)