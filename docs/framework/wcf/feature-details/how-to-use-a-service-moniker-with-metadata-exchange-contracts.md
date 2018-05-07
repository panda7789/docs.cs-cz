---
title: 'Postupy: použití Monikeru služby s kontrakty Metadata Exchange'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Postupy: použití Monikeru služby s kontrakty Metadata Exchange
Po vývoj některé nové služby WCF, můžete rozhodnout, že chcete být schopni volání tyto služby ze skriptu nebo aplikace Visual Basic 6.0. Jedno z těchto metod bude generovat sestavení klienta WCF, registraci sestavení modelu COM, který nainstaluje sestavení v mezipaměti GAC a pak odkazovat typy modelu COM z kódu jazyka Visual Basic. Když distribuujete aplikace, budete muset distribuovat také sestavení klienta WCF. Uživatel pak bude mít k registraci sestavení klienta WCF u modelu COM a jeho následné uložení do mezipaměti GAC. Zprostředkovatel komunikace s objekty WCF COM také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na sestavení klienta WCF. Monikeru služby WCF můžete volat libovolnou službu WCF z jakéhokoli jazyka kompatibilní COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) tak, že zadáte exchange (Mex) koncový bod metadat identifikátor URI, který monikeru služby se používá k extrakci typu informace o službě. Toto téma popisuje, jak volat ukázku získávání spuštění WCF pomocí Přezdívka WCF, který určuje koncový bod Mex.  
  
> [!NOTE]
>  Ve skutečnosti instance typů front definovaných sestavením klienta WCF. Sestavení se používá pouze pro metadata.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Použití monikeru služby s adresou Mex  
  
1.  Sestavit ukázku Začínáme a aplikaci Internet Explorer a přejděte do jeho adresa URL (http://localhost/ServiceModelSamples/Service.svc) zajistit, že služba funguje.  
  
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
