---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: d64be95f71f840e08ede63e1c1f14ee08e52ce97
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592473"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator je nástroj, který můžete použít k vystavení vlastních implementací kanálu do konfiguračního systému. To umožňuje uživatelům vašeho vlastního kanálu nakonfigurovat svůj kanál pomocí souboru. config stejným způsobem, jako by nakonfigurovali systémově poskytované vazby, jako je například `NetTcpBinding` nebo vlastní vazba pomocí `TcpTransportBindingElement` .  
  
 Při psaní vlastního kanálu a jeho zpřístupnění pro programovací model pomocí nového `BindingElement` nebo `Binding` , je nutné vytvořit sadu tříd pro vytvoření `BindingElement` nebo `Binding` konfiguraci pomocí souboru. config. Pomocí nástroje ConfigurationCodeGenerator můžete tyto třídy vygenerovat a rozšířit možnosti svého zákazníka.  
  
### <a name="to-build-the-tool"></a>Sestavení nástroje  
  
1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
2. Sestavení řešení generuje jeden soubor: ConfigurationCodeGenerator. exe. Soubor SampleRun. cmd obsahuje vzorový příkazový řádek, který ukazuje, jak tento nástroj použít k vygenerování tříd pro příklad [Transport: UDP](transport-udp.md) .  
  
### <a name="to-run-the-tool"></a>Spuštění nástroje  
  
1. Pokud máte vlastní `BindingElement` typ i vlastní typ, zadejte na příkazovém řádku následující příkaz `Binding` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Pokud máte pouze vlastní typ, zadejte následující `BindingElement` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Pokud máte pouze vlastní typ, zadejte následující `Binding` :  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Příkaz vygeneruje tři soubory. cs pro `BindingElement` (Pokud jste zadali možnost/BE:), pět souborů cs pro standardní `Binding` (Pokud jste zadali možnost/Sb:) a souboru. XML.  
  
    1. Pokud jste použili možnost/BE, jeden ze souborů. cs implementuje rozhraní `BindingElementExtensionSection` pro váš element vazby. Tento kód zpřístupňuje `BindingElement` systém konfigurace, aby ostatní vlastní vazby mohly použít váš element vazby. Ostatní soubory mají třídy, které reprezentují výchozí hodnoty a konstanty. Soubory obsahují komentáře, které vám umožní `//TODO` připomenout, abyste aktualizovali výchozí hodnoty.  
  
    2. Pokud jste zadali možnost/Sb, dva ze souborů. cs implementují a v `StandardBindingElement` `StandardBindingCollectionElement` uvedeném pořadí zpřístupňují standardní vazbu na konfigurační systém. Ostatní soubory mají třídy, které reprezentují výchozí hodnoty a konstanty. Soubory obsahují komentáře, které vám umožní `//TODO` připomenout, abyste aktualizovali výchozí hodnoty.  
  
         Pokud jste zadali možnost/Sb: parametr CodeToAddTo \<*YourStdBinding*> . cs obsahuje kód, který musíte ručně přidat do třídy, která implementuje standardní vazbu.  
  
     Soubor SampleConfig. XML obsahuje konfigurační kód, který je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozích krocích 1 nebo 2.  
