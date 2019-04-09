---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 7625060cd0512bb7498a931d7b93a731e52c9f00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195186"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator je nástroj, který můžete použít ke zveřejnění vašeho vlastního kanálu implementace konfigurační systém. To umožňuje uživatelům vlastní kanál konfigurovat kanál pomocí souboru .config, stejně jako poskytnutými systémem vazby, jako by konfigurace `NetTcpBinding` nebo vlastní vazby pomocí `TcpTransportBindingElement`.  
  
 Při zápisu vlastního kanálu a zpřístupnit ji programovací model s použitím nového `BindingElement` nebo `Binding`, musíte vytvořit sadu tříd, aby `BindingElement` nebo `Binding` umožňovat konfiguraci pomocí souboru .config. Nástroj ConfigurationCodeGenerator můžete použít ke generování těchto tříd a vylepšení prostředí pro vaše zákazníky.  
  
### <a name="to-build-the-tool"></a>K sestavení nástroj  
  
1.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Sestavování řešení se generuje jeden soubor: ConfigurationCodeGenerator.exe. Ukázka příkazového řádku, který ukazuje, jak tento nástroj používat ke generování třídy pro má soubor SampleRun.cmd [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.  
  
### <a name="to-run-the-tool"></a>Chcete-li spustit nástroj  
  
1.  Na příkazovém řádku zadejte následující, pokud máte i vlastní `BindingElement` typu a vlastní `Binding` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Nebo zadejte následující příkaz, pokud máte jenom vlastní `BindingElement` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Nebo zadejte následující příkaz, pokud máte jenom vlastní `Binding` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Příkaz generuje pro tři soubory .cs `BindingElement` (Pokud jste zadali / být: možnost), pět souborů .cs standardu `Binding` (Pokud jste zadali /sb: možnost) a souboru .xml.  
  
    1.  Pokud jste použili možnost /be, jeden z cs soubory implementuje `BindingElementExtensionSection` pro vaše element vazby. Tento kód poskytuje vaše `BindingElement` konfigurace systému, aby další vlastní vazby můžete použít vaše element vazby. Třídy, které představují výchozí hodnoty a konstanty mají jiné soubory. U souborů `//TODO` komentáře vám aktualizovat výchozí hodnoty.  
  
    2.  Pokud jste určili možnost /sb, dva soubory .cs implementovat `StandardBindingElement` a `StandardBindingCollectionElement` , která zveřejní vaše standardní vazby na konfigurační systém. Třídy, které představují výchozí hodnoty a konstanty mají jiné soubory. U souborů `//TODO` komentáře vám aktualizovat výchozí hodnoty.  
  
         Pokud jste zadali /sb: možnost CodeToAddTo\<*YourStdBinding*> .cs obsahuje kód, který je třeba ručně přidat do třídy, která implementuje standardní vazbu.  
  
     SampleConfig.xml soubor obsahuje kód konfigurace, který je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozím kroku 1 nebo 2.  
