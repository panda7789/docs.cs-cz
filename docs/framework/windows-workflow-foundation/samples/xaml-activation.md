---
title: Aktivace XAML
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-activation"></a>Aktivace XAML
Tento příklad ukazuje, jak k hostování deklarativní pracovní postup ve službě IIS. Ukázka je základní pracovní postup volá `EchoService` má jednu operaci.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte k (stránce pro stažení) Chcete-li stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete řešení XAMLActivation.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení stisknutím **F5**.  
  
3.  Spusťte WcfTestClient.exe. Z příkazového řádku zadejte následující:  
  
    1.  CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE sady Visual Studio  
  
    2.  Spusťte WcfTestClient.exe.  
  
4.  Stisknutím kombinace kláves CTRL + SHIFT + A a nastavení adresu služby nastavte adresu služby na WcfTestClient.exe http://localhost:56133/Service.xamlx.  
  
5.  Provedení operace echo testování služby.  
  
6.  Nasazení služby ve službě IIS pomocí DeployToIIS.Bat v příkazovém řádku s oprávněními správce.  
  
7.  Aktualizujte adresu služby v klientovi http://localhost/XAMLActivation/Service.xamlx a testovat službu znovu pomocí WcfTestClient.exe.
