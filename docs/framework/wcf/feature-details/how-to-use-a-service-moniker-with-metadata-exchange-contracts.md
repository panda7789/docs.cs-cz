---
title: 'Postupy: Použití monikeru služby u kontraktů výměny metadat'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 04a940a6e8f010e5cd851684c5fc62bab2a1a034
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601163"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>Postupy: Použití monikeru služby u kontraktů výměny metadat
Po vývoji některých nových služeb WCF se můžete rozhodnout, že chcete být schopni tyto služby volat ze skriptu nebo aplikace Visual Basic 6,0. Jednou z metod by bylo generovat sestavení klienta WCF, zaregistrovat sestavení v modelu COM, nainstalovat sestavení v globální mezipaměti sestavení (GAC) a pak odkazovat na typy modelu COM z kódu Visual Basic. Při distribuci aplikace budete muset distribuovat i sestavení klienta WCF. Uživatel pak bude muset zaregistrovat sestavení klienta WCF pomocí modelu COM a umístit ho do mezipaměti GAC. Zprostředkovatel komunikace s objekty WCF COM také umožňuje provádět stejná volání služby, aniž by se museli spoléhat na sestavení klienta WCF. Moniker WCF umožňuje volat libovolnou službu WCF z jakéhokoli jazyka kompatibilního s modelem COM (Visual Basic, VBScript, jazyk Visual Basic for Application (VBA) atd.) zadáním identifikátoru URI koncového bodu (MEX) metadat, který používá moniker služby k extrakci typů informací o službě. Toto téma popisuje, jak volat ukázku Začínáme WCF pomocí monikeru WCF, který určuje koncový bod mex.  
  
> [!NOTE]
> Typy definované sestavením klienta WCF nejsou ve skutečnosti vytvořeny. Sestavení se používá pouze pro metadata.  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Použití monikeru služby s adresou MEX  
  
1. Sestavte Začínáme Sample a pomocí Internet Exploreru přejděte na jeho adresu URL ( `http://localhost/ServiceModelSamples/Service.svc` ) a ujistěte se, že služba funguje.  
  
2. Vytvořte skript Visual Basic nebo Visual Basic aplikaci, která obsahuje následující kód:  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. Spusťte Visual Basic aplikaci nebo skript.  
  
    > [!NOTE]
    > Služba, kterou voláte, musí vystavit koncový bod mex pro moniker, aby bylo možné číst metadata ze služby. Další informace najdete v tématu [Postup: publikování metadat pro službu pomocí konfiguračního souboru](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).  
  
    > [!NOTE]
    > Pokud je moniker poškozený nebo pokud není služba k dispozici, volání `GetObject` vrátí chybu s názvem neplatná syntaxe.  Pokud se zobrazí tato chyba, ujistěte se, že moniker, který používáte, je správný a služba je k dispozici.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Použití monikeru služby Windows Communication Foundation bez registrace](use-the-wcf-service-moniker-without-registration.md)
- [Postupy: Použití monikeru služby u kontraktů WSDL](how-to-use-a-service-moniker-with-wsdl-contracts.md)
