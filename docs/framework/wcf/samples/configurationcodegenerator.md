---
title: ConfigurationCodeGenerator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb88d7e523c671886e3ccb0fe22d545c616e2289
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator je nástroj, který můžete použít ke zveřejnění vaší implementace vlastní kanál konfigurační systém. To umožňuje uživatelům vlastní kanál nakonfigurovat kanál pomocí souboru .config stejně, jako by nakonfigurovat poskytované systémem vazbu, jako `NetTcpBinding` nebo vlastní vazby pomocí `TcpTransportBindingElement`.  
  
 Při zápisu vlastním kanálu a umístěte ji do programovací model pomocí nové `BindingElement` nebo `Binding`, musíte vytvořit sadu tříd, aby `BindingElement` nebo `Binding` možné konfigurovat pomocí souboru .config. Nástroj ConfigurationCodeGenerator můžete vygenerovat tyto třídy a zajištění lepších možností vašeho zákazníka.  
  
### <a name="to-build-the-tool"></a>K sestavení nástroje  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Sestavování řešení generuje jeden soubor: ConfigurationCodeGenerator.exe. Soubor SampleRun.cmd má ukázka příkazového řádku, který ukazuje, jak tento nástroj používat ke generování tříd [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
### <a name="to-run-the-tool"></a>Chcete-li spustit nástroj  
  
1.  Na příkazovém řádku zadejte následující, pokud máte i vlastní `BindingElement` typ a vlastní `Binding` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Nebo zadejte následující příkaz, pokud máte pouze vlastní `BindingElement` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Nebo zadejte následující příkaz, pokud máte pouze vlastní `Binding` typu:  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Příkaz generuje tři soubory .cs pro `BindingElement` (Pokud jste zadali / být: možnost), pět souborů .cs pro standardní `Binding` (Pokud jste zadali /sb: možnost) a souboru .xml.  
  
    1.  Pokud jste použili možnost /be, jeden .cs soubory implementuje `BindingElementExtensionSection` pro vaše prvku vazby. Tento kód zpřístupní vaše `BindingElement` konfigurace systému, můžete použít, aby další vlastní vazby vaší prvku vazby. Ostatní soubory mají tříd, které představují výchozí hodnoty a konstanty. U souborů `//TODO` komentáře a tak poznáte, chcete-li aktualizovat výchozí hodnoty.  
  
    2.  Pokud jste zadali možnost /sb, dva soubory .cs implementovat `StandardBindingElement` a `StandardBindingCollectionElement` , který zpřístupňuje vaše standardní vazby v konfiguraci systému. Ostatní soubory mají tříd, které představují výchozí hodnoty a konstanty. U souborů `//TODO` komentáře a tak poznáte, chcete-li aktualizovat výchozí hodnoty.  
  
         Pokud jste zadali /sb: možnost CodeToAddTo\<*YourStdBinding*> .cs má kód, který je třeba ručně přidat do třídy, který implementuje standardní vazbě.  
  
     Soubor SampleConfig.xml obsahuje kód konfigurace, které je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozím kroku, 1 nebo 2.  
  
## <a name="see-also"></a>Viz také
