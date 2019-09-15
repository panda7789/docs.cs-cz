---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990056"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator je nástroj, který můžete použít k vystavení vlastních implementací kanálu do konfiguračního systému. To umožňuje uživatelům vašeho vlastního kanálu nakonfigurovat svůj kanál pomocí souboru. config stejným způsobem, jako by nakonfigurovali systémově poskytované vazby, jako je například `NetTcpBinding` nebo vlastní vazba `TcpTransportBindingElement`pomocí.  
  
 Při psaní vlastního kanálu a jeho zpřístupnění pro programovací model `BindingElement` pomocí nového nebo `Binding`, je nutné vytvořit sadu tříd pro `BindingElement` vytvoření nebo `Binding` konfiguraci pomocí souboru. config. Pomocí nástroje ConfigurationCodeGenerator můžete tyto třídy vygenerovat a rozšířit možnosti svého zákazníka.  
  
### <a name="to-build-the-tool"></a>Sestavení nástroje  
  
1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Sestavení řešení generuje jeden soubor: ConfigurationCodeGenerator.exe. Soubor SampleRun. cmd obsahuje vzorový příkazový řádek, který ukazuje, jak tento nástroj použít k vygenerování tříd pro [přenos: Ukázka](../../../../docs/framework/wcf/samples/transport-udp.md) UDP  
  
### <a name="to-run-the-tool"></a>Spuštění nástroje  
  
1. Pokud máte vlastní `BindingElement` typ i vlastní `Binding` typ, zadejte na příkazovém řádku následující příkaz:  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Pokud máte pouze vlastní `BindingElement` typ, zadejte následující:  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Pokud máte pouze vlastní `Binding` typ, zadejte následující:  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Příkaz vygeneruje tři soubory. cs pro `BindingElement` (Pokud jste zadali možnost/BE:), pět souborů cs pro standardní `Binding` (Pokud jste zadali možnost/Sb:) a souboru. XML.  
  
    1. Pokud jste použili možnost/BE, jeden ze souborů. cs implementuje rozhraní `BindingElementExtensionSection` pro váš element vazby. Tento kód zpřístupňuje `BindingElement` systém konfigurace, aby ostatní vlastní vazby mohly použít váš element vazby. Ostatní soubory mají třídy, které reprezentují výchozí hodnoty a konstanty. Soubory obsahují `//TODO` komentáře, které vám umožní připomenout, abyste aktualizovali výchozí hodnoty.  
  
    2. Pokud jste zadali možnost/Sb, dva ze souborů. cs implementují `StandardBindingElement` `StandardBindingCollectionElement` a v uvedeném pořadí zpřístupňují standardní vazbu na konfigurační systém. Ostatní soubory mají třídy, které reprezentují výchozí hodnoty a konstanty. Soubory obsahují `//TODO` komentáře, které vám umožní připomenout, abyste aktualizovali výchozí hodnoty.  
  
         Pokud jste zadali parametr/Sb: CodeToAddTo\<*YourStdBinding*>. cs má kód, který musíte ručně přidat do třídy, která implementuje standardní vazbu.  
  
     Soubor SampleConfig. XML obsahuje konfigurační kód, který je nutné přidat do konfiguračního souboru, který registruje obslužné rutiny definované v předchozích krocích 1 nebo 2.  
