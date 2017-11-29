---
title: "Kryptografická flexibilita v zabezpečení WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b07b23f4428053964fa33150c4300645242f918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a>Kryptografická flexibilita v zabezpečení WCF
Tento příklad ukazuje, jak určit v algoritmu standardní nebo vlastní k zajištění kryptografických agilní implementace v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta a služby. Ukázka se skládá z následujících projektech:  
  
 Služba  
 Toto je vlastním hostováním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která implementuje `ICalculator` rozhraní a zabezpečuje koncový bod pomocí <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> s zabezpečené relace a spolehlivé relace zakázán. Služba definuje vlastní `SecurityAlgorithmSuite` třídu k určení kryptografické algoritmy, které má být použit pro zabezpečení zpráv.  
  
 Klient  
 Toto je [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]klienta, který službu používá po úspěšném ověření. Vyvolá operace vystavené `ICalculator` rozhraní a implementují službu. Klient také definuje stejné vlastní `SecurityAlgorithmSuite` třídu k určení kryptografické algoritmy, které má být použit pro zabezpečení zpráv.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Otevřete řešení CryptoAgility.sln v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.  
  
3.  Otevřete [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce service.exe kliknete pravým tlačítkem a výběrem **spustit jako správce**.  
  
4.  Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
