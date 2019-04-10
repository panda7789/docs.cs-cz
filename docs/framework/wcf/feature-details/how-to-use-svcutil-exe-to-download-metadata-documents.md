---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: cc9fc4acaeafe4583b1e85a24cab97af1689c638
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328345"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe
Svcutil.exe můžete použít ke stažení metadat z službami a k uložení metadat do místních souborů. Pro schémata HTTP a HTTPS URL Svcutil.exe pokusí se načíst metadata pomocí WS-MetadataExchange a [zjišťování webové služby XML](https://go.microsoft.com/fwlink/?LinkId=94950). Pro všechny ostatní schémata URL Svcutil.exe používá pouze WS-MetadataExchange.  
  
 Ve výchozím nastavení používá Svcutil.exe vazeb definovaných v <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy. Ke konfiguraci vazby používá pro WS-MetadataExchange, je nutné definovat koncový bod klienta v konfiguračním souboru pro Svcutil.exe (svcutil.exe.config), který používá `IMetadataExchange` kontrakt a, který má stejný název jako identifikátor URI (Uniform Resource) schéma adresu koncového bodu metadat.  
  
> [!CAUTION]
> Při spuštění Svcutil.exe k získání metadat pro službu, která poskytuje dva různé služby je smlouvách, že každý obsahuje operace se stejným názvem, Svcutil.exe zobrazí chyba s oznámením, "Nelze získat Metadata z..." Například, pokud máte službu, která zveřejňuje kontrakt služby s názvem `ICarService` , který má operace `Get(Car c)` a ve stejné službě zpřístupňuje kontrakt služby s názvem `IBookService` , který má operace `Get(Book b)`. Chcete-li tento problém obejít, proveďte jednu z následujících akcí:
>
> - Po přejmenování jedné z operací.
> - Nastavte <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na jiný název.
> - Jeden z oborů názvů operace nastavenou na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Chcete-li stáhnout metadata pomocí Svcutil.exe  
  
1. Vyhledejte nástroje Svcutil.exe v následujícím umístění:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. Na příkazovém řádku spusťte nástroj v následujícím formátu.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Je nutné zadat `/t:metadata` možnost stažení metadat. V opačném případě se generují kód klienta a konfigurace.  
  
3. <`url`> Argument určuje adresu URL koncového bodu služby, která poskytuje metadata nebo k dokumentu metadat hostované online. <`epr`> Argument určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.  
  
 Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz soubory ke stažení dokumentů metadat ze spuštěné služby.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
