---
title: "Kodér bajtového datového proudu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7663e0c0073110c0df2e3ece20c240af46a61e92
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="bytestream-encoder"></a>Kodér bajtového datového proudu
Tento příklad ukazuje, jak vytvořit `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> který předvádí funkce encoder datového proudu bajtů.  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje, jak vytvořit standard <xref:System.ServiceModel.Channels.Binding> používání prvky standardní vazby <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Tento příklad ukazuje způsob použití kodér datového proudu bajtů nahrávání a stahování bitovou kopii. Funkce encoder datového proudu bajtů podporuje pouze přenos HTTP a nepodporuje funkce, jako je spolehlivé zasílání zpráv nebo zabezpečení. Jediným <xref:System.ServiceModel.Channels.MessageVersion> podporována je <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Pokud používáte této ukázce [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] nebo [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ujistěte se, že používáte [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] se zvýšenými oprávněními.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete soubor ByteStreamHttpBinding.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Spusťte novou instanci třídy ByteStreamHttpBindingServer projektu kliknutím pravým tlačítkem na projekt v Průzkumníku řešení a výběrem **ladění**a potom **spustit novou instanci** v místní nabídce.  
  
3.  Spusťte novou instanci třídy ByteStreamHttpBindingClient projektu kliknutím pravým tlačítkem na projekt v Průzkumníku řešení a výběrem **ladění**, **spustit novou instanci** v místní nabídce.
