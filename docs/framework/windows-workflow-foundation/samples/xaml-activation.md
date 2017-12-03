---
title: Aktivace XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ac691e3d24e3526b43a6818fbe6bbb33a3375a7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="xaml-activation"></a>Aktivace XAML
Tento příklad ukazuje, jak k hostování deklarativní pracovní postup ve službě IIS. Ukázka je základní pracovní postup volá `EchoService` má jednu operaci.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete řešení XAMLActivation.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím **F5**.  
  
3.  Spusťte WcfTestClient.exe. Z příkazového řádku zadejte následující:  
  
    1.  CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE sady Visual Studio  
  
    2.  Spusťte WcfTestClient.exe.  
  
4.  Nastavte adresu služby na WcfTestClient.exe stisknutím kláves CTRL + SHIFT + A a nastavení http://localhost:56133/Service.xamlx adresu služby.  
  
5.  Provedení operace echo testování služby.  
  
6.  Nasazení služby ve službě IIS pomocí DeployToIIS.Bat v příkazovém řádku s oprávněními správce.  
  
7.  Aktualizujte adresu služby v klientovi http://localhost/XAMLActivation/Service.xamlx a testovat službu znovu pomocí WcfTestClient.exe.
