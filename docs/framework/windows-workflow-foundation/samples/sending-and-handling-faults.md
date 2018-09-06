---
title: Odesílání a zpracování chyb
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800992"
---
# <a name="sending-and-handling-faults"></a>Odesílání a zpracování chyb
Tato ukázka předvádí, jak používat <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> zasílání zpráv aktivity pro odesílání a přijímání očekávaným způsobem a neočekávané chyby. V tomto scénáři první klient vyžádat výsledky v očekávané chybu, která obsahuje její <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekce. Další několik požadavků klientů za následek příjem neočekávané chyby, před posledním neproběhne.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.  
  
2.  Otevřete soubor řešení Faults.sln.  
  
3.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
4.  Spusťte projekt služby.  
  
    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `FaultService` projektu a vyberte **nastavit jako spouštěný projekt**.  
  
    2.  Stisknutím kláves CTRL + F5.  
  
5.  Otevřete jinou kopii [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberete **spustit jako správce**.  
  
6.  Otevřete soubor řešení Faults.sln.  
  
7.  Spuštění klientského projektu.  
  
    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `FaultClient` projektu a vyberte **nastavit jako spouštěný projekt**.  
  
    2.  Stisknutím kláves CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`