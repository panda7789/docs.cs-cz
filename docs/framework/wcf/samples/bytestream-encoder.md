---
title: Kodér bajtového datového proudu
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: ab9ccf47527dcf7f01f272f09b3b341d30fbd8d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete soubor ByteStreamHttpBinding.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Spusťte novou instanci třídy ByteStreamHttpBindingServer projektu kliknutím pravým tlačítkem na projekt v Průzkumníku řešení a výběrem **ladění**a potom **spustit novou instanci** v místní nabídce.  
  
3.  Spusťte novou instanci třídy ByteStreamHttpBindingClient projektu kliknutím pravým tlačítkem na projekt v Průzkumníku řešení a výběrem **ladění**, **spustit novou instanci** v místní nabídce.
