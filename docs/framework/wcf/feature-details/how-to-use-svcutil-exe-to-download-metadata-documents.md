---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: a8872bbf04e688906fb0229e3d8215fb92cdbc3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe
Můžete Svcutil.exe stáhnout metadata z službami a uložit metadata pro místní soubory. Pro schémata HTTP a adresy URL HTTPS, Svcutil.exe pokusí se načíst metadata pomocí protokolu WS-MetadataExchange a [zjišťování webové služby XML](http://go.microsoft.com/fwlink/?LinkId=94950). Pro všechny ostatní schémata URL používá Svcutil.exe pouze WS-MetadataExchange.  
  
 Ve výchozím nastavení používá Svcutil.exe vazeb definovaných v <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy. Ke konfiguraci vazby používá pro WS-MetadataExchange, je nutné definovat koncový bod klienta v konfiguračním souboru pro Svcutil.exe (svcutil.exe.config) používající `IMetadataExchange` kontrakt a který má stejný název jako identifikátoru URI (Uniform Resource) schéma adresa koncového bodu metadat.  
  
> [!CAUTION]
>  Při spuštění Svcutil.exe se získat metadata pro službu, která zpřístupňuje dva různé službu měnící, každý obsahovat operace se stejným názvem, Svcutil.exe zobrazí chyba s oznámením, "Nelze získat Metadata z..." Například pokud máte služby, která zveřejňuje kontrakt služby s názvem ICarService, který má operace získání (Car c) a stejnou službu zpřístupní kontrakt služby s názvem IBookService, který má operace Get (kniha b). Chcete-li tento problém obejít, proveďte jednu z následujících akcí:  
>   
>  -   Přejmenujte jeden z operace  
> -   Nastavte <xref:System.ServiceModel.OperationContractAttribute.Name%2A> na jiný název.  
> -   Jeden z oborů názvů na operace nastavenou na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Chcete-li stáhnout metadat pomocí Svcutil.exe  
  
1.  Vyhledejte nástroje Svcutil.exe v následujícím umístění:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  Na příkazovém řádku spusťte nástroj pomocí formátu.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Je nutné zadat `/t:metadata` možnost stáhnout metadata. Jinak se generuje kód klienta a konfigurace.  
  
3.  <`url`> Argument určuje adresu URL pro koncový bod služby, který poskytuje metadata nebo k dokumentu metadat hostované online. <`epr`> Argument určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby, který podporuje WS-MetadataExchange.  
  
 Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Příklad  
 Tento příkaz stáhne dokumenty metadat spuštěné služby.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
