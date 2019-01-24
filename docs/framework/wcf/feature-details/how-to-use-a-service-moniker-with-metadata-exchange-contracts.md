---
title: 'Postupy: Použití monikeru služby u kontraktů Metadata Exchange'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: e7c05bb43b7811d4716a225142dd880886586783
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495092"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Postupy: Použití monikeru služby u kontraktů Metadata Exchange
Po vývoj některé nové služby WCF, může rozhodnout, že chcete mít možnost volat tyto služby ze skriptu nebo aplikace v jazyce Visual Basic 6.0. Jednu metodu bude generovat sestavení klienta WCF, zaregistrovat sestavení s modelem COM, instalaci sestavení v GAC a pak odkazování na typy modelu COM z kódu jazyka Visual Basic. Pokud distribuujete aplikaci, budete muset distribuovat na klienta WCF sestavení. Uživatel pak muset zaregistrovat sestavení klienta WCF s modelem COM a jeho následné uložení do mezipaměti GAC. Komunikace s objekty COM WCF také umožňuje provádět stejné volání služby bez nutnosti spoléhat se na sestavení klienta WCF. Monikeru služby WCF umožňuje volat libovolnou službu WCF z jakéhokoli jazyka kompatibilního s modelu COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) a tak dále) tak, že zadáte identifikátor URI, který používá monikeru služby k extrakci typů exchange (Mex) koncových bodů metadat informace o službě. Toto téma popisuje, jak volat získávání WCF spuštění ukázky použití monikeru služby WCF, který určuje koncový bod Mex.  
  
> [!NOTE]
>  Typy definované v sestavení klienta WCF se nikdy skutečně vytvořena instance. Sestavení se používá jenom pro metadata.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Použití monikeru služby u adresa MEX.  
  
1.  Ukázka Začínáme vytvářet a používat prohlížeč Internet Explorer a přejděte na její adresu URL (http://localhost/ServiceModelSamples/Service.svc) zajistit, služba funguje.  
  
2.  Vytvořte skript jazyka Visual Basic nebo Visual Basic aplikací, který obsahuje následující kód:  
  
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
    >  Na službu, kterou voláte musí vystavit koncový bod Mex pro moniker bude moct číst metadata ze služby. Další informace najdete v tématu [jak: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    >  Pokud je moniker je poškozený nebo pokud služba není dostupná, volání `GetObject` vrátí chyba s oznámením "Neplatnou syntaxi."  Pokud se zobrazí tato chyba, ujistěte se, že zástupný název, který používáte, je správná a služba není k dispozici.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Použití Monikeru služby Windows Communication Foundation bez registrace](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [Postupy: Použití Monikeru služby u kontraktů WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
