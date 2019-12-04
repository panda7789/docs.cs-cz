---
title: 'Postupy: Vytvoření vlastní šablony aktivity'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: f910d1367c941dbc319421d402cae8f4194872e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715257"
---
# <a name="how-to-create-a-custom-activity-template"></a>Postupy: Vytvoření vlastní šablony aktivity

Vlastní šablony aktivit slouží k přizpůsobení konfigurace aktivit, včetně vlastních složených aktivit, aby uživatelé nemuseli vytvářet jednotlivé aktivity jednotlivě a nakonfigurovali jejich vlastnosti a další nastavení ručně. Tyto vlastní šablony mohou být k dispozici v sadě **nástrojů** na Návrhář postupu provádění systému Windows nebo v přehostujícím návrháři, ze kterých je uživatelé mohou přetáhnout na předem nakonfigurovanou návrhovou plochu. Návrhář postupu provádění lodí s dobrými příklady takových šablon: [Návrhář šablony SendAndReceiveReply](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [Návrhář šablon ReceiveAndSendReply](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v kategorii [Návrháři aktivity zasílání zpráv](/visualstudio/workflow-designer/messaging-activity-designers) .

 První postup v tomto tématu popisuje, jak vytvořit šablonu vlastní aktivity pro aktivitu **zpoždění** a druhá procedura stručně popisuje, jak ji zpřístupnit v Návrhář postupu provádění, abyste ověřili, že vlastní šablona funguje.

 Vlastní šablony aktivit musí implementovat <xref:System.Activities.Presentation.IActivityTemplateFactory>. Rozhraní má jednu <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, pomocí které můžete vytvořit a nakonfigurovat instance aktivit použité v šabloně.

## <a name="to-create-a-template-for-the-delay-activity"></a>Vytvoření šablony pro aktivitu zpoždění

1. Spusťte Visual Studio 2010.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V podokně **typy projektů** vyberte **pracovní postup** z **vizuálních C#**  projektů nebo skupin **Visual Basic** v závislosti na jazykové předvolbách.

4. V podokně **šablony** vyberte **Knihovna aktivit**.

5. Do pole **název** zadejte `DelayActivityTemplate`.

6. Přijměte výchozí hodnoty v textových polích **umístění** a **název řešení** a potom klikněte na tlačítko **OK**.

7. V **Průzkumník řešení** klikněte pravým tlačítkem na adresář odkazy projektu DelayActivityTemplate a výběrem možnosti **Přidat odkaz** otevřete dialogové okno **Přidat odkaz** .

8. Přejděte na kartu **.NET** a vyberte **PresentationFramework** ze sloupce **název součásti** na levé straně a kliknutím na **OK** přidejte odkaz na soubor PresentationFramework. dll.

9. Opakujte tento postup, chcete-li přidat odkazy na soubory System. Activities. Presentation. dll a WindowsBase. dll.

10. Klikněte pravým tlačítkem myši na projekt DelayActivityTemplate v **Průzkumník řešení** a zvolte možnost **Přidat** a poté **Nová položka** . tím otevřete dialogové okno **Přidat novou položku** .

11. Vyberte šablonu **třídy** , pojmenujte ji MyDelayTemplate a pak klikněte na **OK**.

12. Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. Implementujte <xref:System.Activities.Presentation.IActivityTemplateFactory> pomocí `MyDelayActivity` třídy s následujícím kódem. Tím se nakonfiguruje zpoždění na dobu 10 sekund.

    ```csharp
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

14. Vyberte **Sestavit řešení** z nabídky **sestavení** pro vygenerování souboru DelayActivityTemplate. dll.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Zpřístupnění šablony ve Návrhář postupu provádění

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení DelayActivityTemplate a zvolte **Přidat** a pak **Nový projekt** . otevře se dialogové okno **Přidat nový projekt** .

2. Vyberte šablonu **Konzolová aplikace pracovního postupu** , pojmenujte ji `CustomActivityTemplateApp`a potom klikněte na tlačítko **OK**.

3. V **Průzkumník řešení** klikněte pravým tlačítkem na adresář odkazy projektu CustomActivityTemplateApp a výběrem možnosti **Přidat odkaz** otevřete dialogové okno **Přidat odkaz** .

4. Přejděte na kartu **projekty** a vyberte **DelayActivityTemplate** ze sloupce **název projektu** na levé straně a kliknutím na **OK** přidejte odkaz na soubor DelayActivityTemplate. dll, který jste vytvořili v prvním postupu.

5. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt CustomActivityTemplateApp a vyberte **sestavit** pro zkompilování aplikace.

6. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt CustomActivityTemplateApp a vyberte **nastavit jako spouštěný projekt**.

7. Vyberte možnost **Spustit bez ladění** z nabídky **ladění** a stisknutím libovolné klávesy pokračujte po zobrazení výzvy z okna cmd. exe.

8. Otevřete soubor Workflow1. XAML a otevřete **sadu nástrojů**.

9. Vyhledejte šablonu **MyDelayActivity** v kategorii **DelayActivityTemplate** . Přetáhněte ji na návrhovou plochu. V okně **vlastnosti** potvrďte, že vlastnost `Duration` byla nastavena na 10 sekund.

## <a name="example"></a>Příklad
 Soubor MyDelayActivity.cs by měl obsahovat následující kód.

```csharp
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
- [Přizpůsobení prostředí pro návrh pracovního postupu](customizing-the-workflow-design-experience.md)
