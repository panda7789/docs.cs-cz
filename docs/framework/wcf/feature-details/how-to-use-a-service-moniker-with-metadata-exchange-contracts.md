---
title: "Postupy: použití Monikeru služby s kontrakty Metadata Exchange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d2b5b6d4a671a3eb281f49dd60fd3c00ee76f8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Postupy: použití Monikeru služby s kontrakty Metadata Exchange
Po vývoj některé nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, můžete rozhodnout, že chcete být schopni volání tyto služby ze skriptu nebo aplikace Visual Basic 6.0. Jedno z těchto metod bude generovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta zaregistrovat sestavení modelu COM, nainstalujte sestavení v mezipaměti GAC a pak odkazovat typy modelu COM z kódu jazyka Visual Basic. Když distribuujete aplikace, budete ji muset distribuovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] také sestavení klienta. Uživatel pak bude mít k registraci sestavení klienta WCF u modelu COM a jeho následné uložení do mezipaměti GAC. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Zprostředkovatel komunikace s objekty COM také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sestavení klienta. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přezdívka umožňuje volat žádný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby z jakéhokoli jazyka kompatibilní COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) zadáním exchange (Mex) koncový bod metadat identifikátor URI, který používá monikeru služby extrahovat typ informace o službě. Toto téma popisuje, jak volat Začínáme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázkové pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přezdívka, která určuje koncový bod Mex.  
  
> [!NOTE]
>  Typy definované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nikdy skutečně instance sestavení klienta. Sestavení se používá pouze pro metadata.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Použití monikeru služby s adresou Mex  
  
1.  Sestavit ukázku Začínáme a aplikaci Internet Explorer a přejděte do jeho adresa URL (http://localhost/ServiceModelSamples/Service.svc) k zajištění, že služba funguje.  
  
2.  Vytvořte skript jazyka Visual Basic nebo Visual Basic aplikaci, která obsahuje následující kód:  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  Spuštění aplikace Visual Basic nebo skriptu.  
  
    > [!NOTE]
    >  Služby, ke kterému se připojujete musí vystavit koncový bod Mex pro Přezdívka moct číst metadata ze služby. Další informace najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Pokud Přezdívka je poškozený nebo pokud služba není dostupná, volání `GetObject` se vrátí chyba s oznámením "Neplatnou syntaxi."  Pokud se zobrazí tato chyba, ujistěte se, kterou používáte Přezdívka je správný a služba není k dispozici.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití monikeru služby Windows Communication Foundation bez registrace](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [Postupy: Použití monikeru služby u kontraktů WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
