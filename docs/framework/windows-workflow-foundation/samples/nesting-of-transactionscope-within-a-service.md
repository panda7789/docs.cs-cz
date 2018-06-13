---
title: Vnoření TransactionScope v rámci služby
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: 9c556df417548ab348d1dd5bc642928ae68d8878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518266"
---
# <a name="nesting-of-transactionscope-within-a-service"></a>Vnoření TransactionScope v rámci služby
Tato ukázka se skládá z těchto dvou scénářů, spusťte znázorňující způsob zpracování <xref:System.Activities.Statements.TransactionScope> instance aktivit v rámci služby. Nejprve transakce je zahájeno pomocí <xref:System.Activities.Statements.TransactionScope> aktivitu, chcete-li vytvořit novou transakci na straně klienta a <xref:System.ServiceModel.Activities.TransactedReceiveScope> přijmout a obor životnost transakce na serveru. První scénář v rámci služby běží sekundární <xref:System.Activities.Statements.TransactionScope> aktivity k předvedení vnořené <xref:System.Activities.Statements.TransactionScope> aktivity v rámci služby. Druhý scénář popisuje, jak jsou dodržovány vypršení časových limitů v rámci vnořeného <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
## <a name="client-application"></a>Klientské aplikace  
 Klientská aplikace spouští pracovní postup, který spustí <xref:System.Activities.Statements.TransactionScope> aktivity, vytiskne ID distribuované transakce, odešle zprávu do serveru, tok transakce, obdrží odpověď, vytiskne ID distribuované transakce znovu a dokončení. Dělá to jednou pro každý scénář služby.  
  
## <a name="server-application"></a>Aplikace serveru  
 Serverový projekt je hostován v <xref:System.ServiceModel.Activities.WorkflowServiceHost>, která vytvoří koncový bod pro naslouchání zprávu od klienta. Pracovní postup se jedná o <xref:System.ServiceModel.Activities.TransactedReceiveScope>, který sdružení transakcí obdrží z klienta, vytiskne distribuované transakce ID a potom provede druhý <xref:System.Activities.Statements.TransactionScope> aktivity. V první scénář transakce byla úspěšně dokončena. Druhý scénář, text <xref:System.Activities.Statements.TransactionScope> aktivity zpoždění pěti sekund a časový limit pro transakci je nastavená na dvou sekund. Pokud vyprší časový limit transakce transakce byla přerušena.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení TransactionServiceExample.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení proběhla úspěšně, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**. V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **spustit**.  
  
4.  Stisknutím klávesy F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Alternativně můžete stisknutím kláves CTRL + F5 nebo vybrat **spustit bez ladění** z **ladění** nabídku spustit bez ladění.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
