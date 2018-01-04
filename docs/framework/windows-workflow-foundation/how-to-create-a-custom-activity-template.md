---
title: "Postupy: vytvoření vlastní aktivity šablony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 772ad2a7ea56001bf3ecba089e62d6bc0f59e5ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-activity-template"></a>Postupy: vytvoření vlastní aktivity šablony
Vlastní aktivity šablony slouží k přizpůsobení konfigurace aktivit, včetně vlastních složené aktivit, tak, aby uživatelé nebudou mít k vytvoření jednotlivě každou aktivitu a nakonfigurovat jejich vlastnosti a další nastavení ručně. Tyto vlastní šablony může být k dispozici v **sada nástrojů** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] nebo opětovné hostování nástroje návrháře, ze kterého uživatelů můžete přetáhnout na předkonfigurované návrhovou plochu. [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]se dodává s dobrým příkladem takové šablony: [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) a [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) v [návrháře aktivitslužbyzasílánízpráv](/visualstudio/workflow-designer/messaging-activity-designers) kategorie.  
  
 První postup v tomto tématu popisuje, jak vytvořit šablonu vlastní aktivity pro **zpoždění** aktivity a druhý postup stručně popisuje postupy, aby byl k dispozici v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] k ověření, že funguje vlastní šablony.  
  
 Musí implementovat vlastní aktivity šablony <xref:System.Activities.Presentation.IActivityTemplateFactory>. Rozhraní má jeden <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metodu, pomocí kterého můžete vytvořit a nakonfigurovat instance aktivit použít v šabloně.  
  
### <a name="to-create-a-template-for-the-delay-activity"></a>Chcete-li vytvořit šablonu aktivity zpoždění  
  
1.  Spustit [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom vyberte **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **typy projektů** podokně, vyberte **pracovního postupu** buď z **Visual C#** projekty nebo **jazyka Visual Basic** seskupení v závislosti na vaší jazykové předvolby.  
  
4.  V **šablony** podokně, vyberte **knihovna aktivit**.  
  
5.  V **název** zadejte `DelayActivityTemplate`.  
  
6.  Přijměte výchozí hodnoty v **umístění** a **název řešení** textová pole a pak klikněte na tlačítko **OK**.  
  
7.  Klikněte pravým tlačítkem na adresář odkazů projektu DelayActivityTemplate v **Průzkumníku řešení** a zvolte **přidat odkaz na** otevřete **přidat odkaz na** dialogové okno.  
  
8.  Přejděte na **.NET** a vyberte **PresentationFramework** z **název komponenty** sloupce na levé straně a klikněte na **OK** přidáním odkazu k souboru knihovně PresentationFramework.dll.  
  
9. Opakujte tento postup, čímž přidáte odkazy System.Activities.Presentation.dll a knihovně WindowsBase.dll soubory.  
  
10. Klikněte pravým tlačítkem na projekt DelayActivityTemplate **Průzkumníku řešení** a zvolte **přidat** a potom **nová položka** otevřete **přidat novou položku**dialogové okno.  
  
11. Vyberte **třída** název MyDelayTemplate šablony a pak klikněte na **OK**.  
  
12. Otevřete soubor MyDelayTemplate.cs a přidejte následující příkazy.  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. Implementace <xref:System.Activities.Presentation.IActivityTemplateFactory> s `MyDelayActivity` třídy následujícím kódem. Tím se nakonfiguruje zpoždění tak, aby měl v délce 10 sekund.  
  
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
  
14. Vyberte **sestavit řešení** z **sestavení** nabídky pro generování souboru DelayActivityTemplate.dll.  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Chcete-li šablonu k dispozici v Návrháři pracovních postupů  
  
1.  Klikněte pravým tlačítkem na řešení DelayActivityTemplate v **Průzkumníku řešení** a zvolte **přidat** a potom **nový projekt** otevřete **přidat nový projekt** dialogové okno.  
  
2.  Vyberte **pracovního postupu konzolové aplikace** šablony, pojmenujte ji `CustomActivityTemplateApp`a potom klikněte na **OK**.  
  
3.  Klikněte pravým tlačítkem na adresář odkazů projektu CustomActivityTemplateApp v **Průzkumníku řešení** a zvolte **přidat odkaz na** otevřete **přidat odkaz na** dialogové okno pole.  
  
4.  Přejděte na **projekty** a vyberte **DelayActivityTemplate** z **název projektu** sloupce na levé straně a klikněte na **OK** přidat odkaz na soubor DelayActivityTemplate.dll, který jste vytvořili v prvním postupu.  
  
5.  Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp **Průzkumníku řešení** a zvolte **sestavení** kompilace aplikace.  
  
6.  Klikněte pravým tlačítkem na projekt CustomActivityTemplateApp **Průzkumníku řešení** a zvolte **nastavit jako spouštěný projekt**.  
  
7.  Vyberte **spustit bez ladění** z **ladění** nabídky a stiskněte klávesu žádné klíče z okna cmd.exe pokračovat po zobrazení výzvy.  
  
8.  Otevřete soubor Workflow1.xaml a otevřete **sada nástrojů**.  
  
9. Vyhledejte **MyDelayActivity** šablonu **DelayActivityTemplate** kategorie. Přetáhněte ji na návrhovou plochu. Potvrďte v **vlastnosti** okno, `Duration` vlastnost byla nastavena na 10 sekund.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [Přizpůsobení prostředí pro návrh pracovního postupu](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
