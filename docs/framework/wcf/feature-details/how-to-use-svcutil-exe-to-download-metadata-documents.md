---
title: 'Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe'
description: Naučte se, jak pomocí Svcutil.exe stahovat metadata ze spuštěných služeb a ukládat tato metadata do místních souborů.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246763"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe
Pomocí Svcutil.exe můžete stahovat metadata ze spuštěných služeb a ukládat je do místních souborů. V případě schémat URL protokolu HTTP a HTTPS se Svcutil.exe pokusí načíst metadata pomocí funkce WS-MetadataExchange a [zjišťování webové služby XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)). Pro všechna ostatní schémata URL Svcutil.exe používá pouze WS-MetadataExchange.  
  
 Ve výchozím nastavení Svcutil.exe používá vazby definované ve <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě. Pokud chcete nakonfigurovat vazbu použitou pro WS-MetadataExchange, je nutné v konfiguračním souboru pro Svcutil.exe (svcutil.exe.config) definovat koncový bod klienta, který používá `IMetadataExchange` kontrakt a který má stejný název jako schéma identifikátoru URI (Uniform Resource Identifier) adresy koncového bodu metadat.  
  
> [!CAUTION]
> Při spuštění Svcutil.exe k získání metadat pro službu, která zveřejňuje dvě různé kontrakty služby, které obsahují operaci se stejným názvem, Svcutil.exe se zobrazí chyba s oznámením, že nejde získat metadata z.... Například pokud máte službu, která zveřejňuje kontrakt služby s názvem `ICarService` , který má operaci, `Get(Car c)` a stejná služba zveřejňuje kontrakt služby `IBookService` s názvem, který má operaci `Get(Book b)` . Chcete-li tento problém obejít, proveďte jednu z následujících akcí:
>
> - Přejmenujte jednu z operací.
> - Nastavte na <xref:System.ServiceModel.OperationContractAttribute.Name%2A> jiný název.
> - Nastavte jeden z oborů názvů operací na jiný obor názvů pomocí <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> Vlastnosti.
  
## <a name="to-download-metadata-using-svcutilexe"></a>Stažení metadat pomocí Svcutil.exe  
  
1. Vyhledejte nástroj Svcutil.exe v následujícím umístění:  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. Na příkazovém řádku spusťte nástroj v následujícím formátu.  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Je nutné zadat `/t:metadata` možnost stahovat metadata. V opačném případě se generuje kód klienta a konfigurace.  
  
3. Argument <`url`>Určuje adresu URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online. Argument <`epr`> Určuje cestu k souboru XML, který obsahuje WS-Addressing `EndpointAddress` pro koncový bod služby podporující WS-MetadataExchange.  
  
 Další možnosti o použití tohoto nástroje pro stažení metadat najdete v tématu [Nástroj pro nástroj pro metadata ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz stáhne dokumenty metadat z běžící služby.  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
