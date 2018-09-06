---
title: Kodér bajtového datového proudu
ms.date: 03/30/2017
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
ms.openlocfilehash: cbd4110ecc04923b79d6b910fcf7ab4ca2012680
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855449"
---
# <a name="bytestream-encoder"></a>Kodér bajtového datového proudu
Tato ukázka předvádí, jak vytvořit `ByteStreamHttpBinding`, <xref:System.ServiceModel.Channels.Binding> , která ukazuje funkce encoder datového proudu bajtů.  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje, jak vytvořit standardní <xref:System.ServiceModel.Channels.Binding> konkrétně pomocí elementů standardní vazbu <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.HttpTransportBindingElement>. Tento příklad ukazuje způsob použití kodér datového proudu bajtů k nahrání a stažení image. Funkce encoder datového proudu bajtů podporuje pouze přenos pomocí protokolu HTTP a nepodporuje funkce, jako je spolehlivé zasílání zpráv nebo zabezpečení. Jediná <xref:System.ServiceModel.Channels.MessageVersion> podporována je <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Pokud používáte této ukázce [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] nebo [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ujistěte se, že používáte [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] se zvýšenými oprávněními.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Otevřete soubor ByteStreamHttpBinding.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Spustit novou instanci třídy ByteStreamHttpBindingServer projekt tak, že kliknete pravým tlačítkem myši na Průzkumníka řešení a vyberete **ladění**a potom **zahájit novou instanci** v místní nabídce.  
  
3.  Spustit novou instanci třídy ByteStreamHttpBindingClient projekt tak, že kliknete pravým tlačítkem myši na Průzkumníka řešení a vyberete **ladění**, **zahájit novou instanci** v místní nabídce.
