---
title: Odeslání a zpracování chyb
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sending-and-handling-faults"></a>Odeslání a zpracování chyb
Tento příklad znázorňuje způsob použití <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity pro odesílání a přijímání očekávané a neočekávané chyby zasílání zpráv. V tomto scénáři první klient v požadavku má za následek očekávané selhání, který byl zahrnut v jeho <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> kolekce. Další požadavky několik klientů za následek před posledním neproběhne přijetí neočekávané chyby.  
  
## <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.  
  
2.  Otevřete soubor řešení Faults.sln.  
  
3.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
4.  Spusťte projekt služby.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `FaultService` projektu a vyberte **nastavit jako spouštěný projekt**.  
  
    2.  Stisknutím klávesy CTRL + F5.  
  
5.  Otevřete jinou kopii [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] se zvýšenými oprávněními, kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ikonu a vyberte **spustit jako správce**.  
  
6.  Otevřete soubor řešení Faults.sln.  
  
7.  Spuštění klientského projektu.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši `FaultClient` projektu a vyberte **nastavit jako spouštěný projekt**.  
  
    2.  Stisknutím klávesy CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`