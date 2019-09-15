---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 25840247e59b9dd61cadaa2ee94713240d135f88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991605"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe
Pomocí Svcutil. exe můžete stahovat metadata ze spuštěných služeb a ukládat je do místních souborů. V případě schémat URL s protokolem HTTP a HTTPS se Svcutil. exe pokusí načíst metadata pomocí [zjišťování webové služby](https://go.microsoft.com/fwlink/?LinkId=94950)WS-MetadataExchange a XML. Pro všechna ostatní schémata URL používá Svcutil. exe pouze WS-MetadataExchange.  
  
 Ve výchozím nastavení používá Svcutil. exe vazby definované ve <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě. Pokud chcete nakonfigurovat vazbu použitou pro WS-MetadataExchange, musíte v konfiguračním souboru pro Svcutil. exe (Svcutil. exe. config) definovat koncový bod klienta, který používá `IMetadataExchange` kontrakt a který má stejný název jako identifikátor URI (Uniform Resource Identifier). schéma adresy koncového bodu metadat  
  
> [!CAUTION]
> Při spuštění Svcutil. exe za účelem získání metadat pro službu, která zveřejňuje dvě různé kontrakty služby, které obsahují operaci se stejným názvem, Svcutil. exe zobrazí chybu s oznámením, že nelze získat metadata z.... Například pokud máte službu, `ICarService` která zveřejňuje kontrakt služby s názvem, který má operaci `Get(Car c)` , a stejná služba zveřejňuje kontrakt služby s názvem `IBookService` , který má operaci `Get(Book b)`. Chcete-li tento problém obejít, proveďte jednu z následujících akcí:
>
> - Přejmenujte jednu z operací.
> - <xref:System.ServiceModel.OperationContractAttribute.Name%2A> Nastavte na jiný název.
> - Nastavte jeden z oborů názvů operací na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnosti.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Stažení metadat pomocí Svcutil. exe  
  
1. Vyhledejte nástroj Svcutil. exe v následujícím umístění:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. Na příkazovém řádku spusťte nástroj v následujícím formátu.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Je nutné zadat `/t:metadata` možnost stahovat metadata. V opačném případě se generuje kód klienta a konfigurace.  
  
3. Argument <`url`> Určuje adresu URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online. Argument <`epr`> Určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.  
  
 Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz stáhne dokumenty metadat z běžící služby.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
