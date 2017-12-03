---
title: "Nástroje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 174459c23bd6ecd336394146b6d91e265cb820d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="tools"></a>Nástroje
Toto téma uvádí všechny výjimky generované [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nástroje.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|ParametersTarget|\<výčet >|  
|ParametersToolConfig|\<configFile >|  
|ErrInvalidPath|Zadaný je platná cesta UNC. Zkontrolujte zadaného argumentu.|  
|ParametersReference|\<Cesta k souboru >|  
|WrnCannotLoadConfigFileForValidation|Zpracování konfiguračního souboru načíst ze zadaného umístění došlo k chybě. Služby, které jsou definovány v tento konfigurační soubor nelze ověřit.|  
|MoreHelp|Další nápovědu zadejte "svcutil" pomocí zadaných argumentů.|  
|HelpMergeConfig|Způsobí, že generovaný konfigurace do existujícího souboru místo přepsal existující soubor.|  
|ErrCannotWriteFile|Nelze zapisovat do výstupního souboru.|  
|ErrInvalidNamespaceArgument|Zadaná možnost byl předán zadaná neplatná hodnota. Zadejte textový soubor s oddělovači cílový obor názvů a dvojice názvů CLR.|  
|HelpImportXmlType|Nakonfiguruje serializátor kontraktu k importu jiný kontraktu typy jako typy IXmlSerializable.|  
|ErrExclusiveOptionsSpecified|Zadaná možnost nelze použít, pokud zadaná možnost byla zadána.|  
|WrnHttpGetFailed|Chyba protokolu HTTP GET s zadaný identifikátor URI.|  
|ErrInputFileNotAssemblyOrMetadata|Soubor v zadaném umístění číst prostřednictvím zadaného argumentu vstupní nezobrazí jako soubor XML metadata nebo platnou sestavu.|  
|WrnUnknownMetadataFound|Nelze uložit dokument nerozpoznané metadat zadaného typu.|  
|ErrDirectoryContainsInvalidCharacters|Zadaná možnost byl předán zadaná neplatná hodnota. Je zadaný znak není povolené v cestě.|  
|WrnCannotResolveServiceForValidation|Nelze načíst službu s zadaný configName. K ověření služby, zadejte oba sestavení, které obsahuje typ služby a spustitelný soubor s konfigurací pro tuto službu.|  
|ErrUnexpectedValue|Zadaná možnost nepodporuje hodnoty.|  
|#InvalidArg|Zadaný obsahuje neplatný argument.|  
|ParametersExcludeType|\<Typ >|  
|HelpXmlSerializer|Generovat datové typy, které používají třídy XmlSerializer k serializaci a deserializaci.|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|Došlo k chybě v nástroji.|  
|HelpNologo|Zpráva o autorských právech a hlavičku potlačeno.|  
|ErrInputConflictsWithTarget|Typ vstupu pro čtení z určeného nepodporuje Zadaná možnost nastavit na zadanou hodnotu.|  
|WrnCannotLoadServiceForExport|Došlo k chybě při načítání typu služby pro export.|  
|HelpMetadataDownloadCategory|-= STAŽENÍ METADAT =-|  
|WrnNoServiceContractTypes|Nelze vygenerovat třídy XmlSerializer typy pro zadané sestavení. Nebyly nalezeny žádné typy kontrakt služby.|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Došlo k chybě při načítání typy v sestavení, které byla načtena z určeného. Některé typy v sestavení nelze načíst a nejsou k dispozici v nástroji.|  
|ErrDirectoryPointsToAFile|Zadaná možnost byl předán zadaná neplatná hodnota. Zadaná hodnota je cesta k souboru.|  
|Chyba|Chyba:|  
|ErrDuplicateReferenceValues|Zadané sestavení bylo načteno dvakrát pomocí zadané možnosti. Sestavení může být pouze odkaz na jednou.|  
|WrnNoXmlSerializerOperationBehavior|Nelze vygenerovat třídy XmlSerializer pro zadané sestavení. Žádné kontrakt služby v sestavení má operace s XmlSerializerOperationBehavior.|  
|ErrCannotCreateDirectory|Zadaný adresář nelze vytvořit.|  
|ErrCouldNotLoadTypesFromAssemblyAt|Nelze načíst všechny typy v zadaném sestavení.|  
|ErrUnknownSwitch|Zadaný přepínač je nerozpoznanou možnost.|  
|Logo|Logo nástroje je "Microsoft® Service Model metadat nástroj" s verzí.|  
|NoCodeWasGenerated|Žádný kód byl vygenerován.<br /><br /> Pokud chcete generovat klienta, může to být způsobeno dokumenty metadat neobsahoval žádné platné smlouvy ani služby<br /><br /> nebo protože všechny kontrakty nebo služby byly zjištěny existovat v referenční sestavení. Ověřte, nástroj předán všechny dokumenty metadat.|  
|WrnUnableToLoadContractForSGen|Došlo k chybě při načítání typu kontraktu. Nelze vygenerovat typ třídy XmlSerializer pro tento kontrakt. Typ a podrobnosti nejsou zadány.|  
|WrnOptionConflictsWithInput|Zadaná možnost nelze použít s více vstupních sestavení. Zadaná možnost je ignorována.|  
|ErrUnableToImportMetadata|Při pokusu o import metadat došlo ke kritické chybě.|  
|ErrInvalidSerializer|Zadaná možnost byl předán neplatný serializátor hodnotu. Podporované serializátorů nejsou zadány.|  
|SavingDownloadedMetadata|Ukládání souborů stažené metadat...|  
|WrnNoConfigForServices|Žádný z těchto sestavení předán byly spustitelné soubory s konfiguračním souboru nebo žádná z konfigurační soubory obsažené služby s názvem Zadaná konfigurace.|  
|ErrInputConflictsWithOption|Čtení ze zadaného vstupu nelze použít s parametrem zadané, protože jejich implikují různé režimy činnosti nástroje.|  
|ErrUnableToExportEndpoints|Došlo k chybě při exportu zadaný typ služby.|  
|ErrInputSchemaParseError|Schéma XML při analýze došlo k chybě při čtení zadaného. Ověřte, že zadaný kód XML ve správném formátu a platné.|  
|ErrInputPolicyParseError|Při čtení zadaného došlo k chybě analýzy WS-Policy. Ověřte, že zadaný kód XML ve správném formátu a platné.|  
|ErrUnableToLoadReferenceType|Došlo k chybě při načítání typu odkazované kontrakt. Tento zadaný typ se ignoruje.|  
|WrnCannotLoadServiceForValidation|Došlo k chybě při načítání službu, kterou chcete ověřit. Typ a podrobnosti nejsou zadány.|  
|HelpCodeGenerationCategory|-= GENEROVÁNÍ KÓDU =-|  
|RetreivingMetadataWithMexAndDisco|Probíhá pokus o stažení metadat ze zadaného pomocí protokolu WS-Metadata Exchange nebo DISCO.|  
|ErrGeneralSchemaValidation|Došlo k chybě při ověřování schémat XML, které byly vygenerovány během exportu.|  
|ParametersDirectory|\<adresář >|  
|ErrCannotLoadSpecifiedType|Zadaná hodnota, která byla předána Zadaná možnost mohou být načteny žádné typu. Zkontrolujte, zda je sestavení, které patří tento typ zadán pomocí zadané možnosti.|  
|ErrOptionModeConflict|Zadaná možnost nelze použít s parametrem zadané, protože jejich implikují typy odlišný výstup.|  
|ErrIsNotAnAssembly|Nelze načíst zadaný jako sestavení. Ověřte, že tento soubor sestavení .NET.|  
|ErrInputConflictsWithMode|Čtení ze zadaného vstupu není konzistentní s dalšími možnostmi.|  
|ErrDuplicateValuePassedToTypeArg|Zadaná hodnota byl předán Zadaná možnost vícekrát. Každý typ lze zadat pouze jednou.|  
|ErrInputEPRFileParseError|Reference koncového bodu nelze číst ze zadaného. Ověřte, že zadaný kód XML ve správném formátu a platné.|  
|ErrCouldNotCreateCodeProvider|Pro zadanou hodnotu, která byla předána /{1} argument nelze vytvořit zprostředkovatel kódu. Ověřte, zda je správně nainstalován a nakonfigurován zprostředkovatele kódu.|  
|ErrPathTooLongDirOnly|Výsledná zadaná cesta je příliš dlouhý. Zkontrolujte zadaného argumentu.|  
|HelpDataContractSerializer|Generovat datové typy, které používají serializátor kontraktu k serializaci a deserializaci.|  
|ErrUnableToExportEndpoint|Došlo k chybě při exportu název zadaný koncový bod v určeném oboru názvů v zadaný typ služby nalezen v konfiguračním souboru načten pro sestavení.|  
|HelpUsage1|Zobrazí nápovědu využití.|  
|HelpUsage2|Zobrazí nápovědu využití.|  
|HelpUsage3|Zobrazí nápovědu využití.|  
|HelpUsage4|Zobrazí nápovědu využití.|  
|HelpUsage5|Zobrazí nápovědu využití.|  
|ErrDirectoryNotFound|Zadaný adresář nebyl nalezen. Ověřte, zda adresář existuje a zda máte příslušná oprávnění k jeho čtení.|  
|ErrUnableToLoadFile|Zadaný soubor nelze přečíst.|  
|ErrNoFilesFound|Zadaná vstupní cesta k odkazování na všechny existující soubory nezobrazí.|  
|ParametersConfig|\<configFile >|  
|ErrDirectoryInsteadOfFile|Zadaná vstupní cesta pravděpodobně adresáře. Je třeba adresy URL nebo cesty k souborům.|  
|HelpConfig|Dá pokyn, nástroje pro generování konfigurační soubor se zadaným názvem. Výchozí: output.config.|  
|ErrSingleUseSwitch|Zadaná možnost nelze zadat více než jednou.|  
|Upozornění|Upozornění:|  
|WrnAmbiguousServiceConfig|Podle zadaný název konfigurace bylo nalezeno více konfigurace služby, jsou specifikovány následující sestavení.|  
|ErrInvalidInputPath|Zadaná vstupní cesta k odkazování na všechny existující soubory se nezobrazí a nezdá se být platný identifikátor URI.|  
|ErrUnableToLoadInputs|Došlo k chybě při čtení načíst metadata.|  
|GeneratingSerializer|Vytváření XML serializátorů...|  
|HelpToolConfig|Vlastní konfigurační soubor používejte místo konfiguračního souboru aplikace. Tímto lze změnit konfiguraci metadata nebo zaregistrovat rozšíření konfigurace beze změny nástroje konfigurační soubor.|  
|ErrValidateInvalidUse|Zadaná možnost nelze použít s Zadaná možnost.|  
|WrnWSMExFailed|Chyba WS-Metadata Exchange s zadaný identifikátor URI.|  
|HelpNoconfig|Nevydávají konfigurace.|  
|HelpCodeGenerationDescription|Zadaný seznam může generovat typy kontraktů, klientů a dat služby z dokumentů metadat.|  
|HelpTargetMetadata|Výstup metadat. Pokud vstup je adresa URL, Svcutil.exe uloží metadata na disk a nevygeneruje žádný kód. Pokud vstup je jeden nebo více sestavení, vygeneruje Svcutil.exe metadata z typů v sestaveních.|  
|ErrAmbiguousOptionModeConflict|Zadaná možnost v konfliktu s jinými možnostmi. Kontrolovat používání nástroje.|  
|ErrNotLanguageOrCodeDomType|Zadaná hodnota, která byla předána zadaného argumentu nepředstavuje definované jazyk a nebylo možné načíst jako plně kvalifikovaný typ CLR.|  
|ErrUnableToUniquifyFilename|Název výstupního souboru nelze vytvořit. Příliš mnoho souborů se vytváří se zadanou předponou.|  
|ErrCannotCreateFile|Zadaný výstupní soubor nelze vytvořit.|  
|ErrExpectedValue|Zadaná možnost vyžaduje, aby byl specifikován hodnotu.|  
|ErrCannotDisambiguateSpecifiedTypes|Více než jeden typ se stejným názvem existuje v sadě odkazované sestavení. Pomocí názvů kvalifikovaný sestavení k rozlišení mezi typy zadaný pro zadaná možnost.|  
|RetreivingMetadataWithMexOnly|Probíhá pokus o stažení metadat ze zadaného umístění pomocí protokolu WS-Metadata Exchange. Tato adresa URL DISCO nepodporuje.|  
|ErrInvalidTarget|Zadaný cíl je platný, pokud je zadán pomocí Zadaná možnost. Podporované cíle nejsou zadány.|  
|ErrPathTooLong|Výsledná cesta je příliš dlouhá. Zkontrolujte zadané argumenty.|  
|HelpCommonOptionsCategory|-= BĚŽNÉ MOŽNOSTI =-|  
|ParametersServiceName|\<serviceConfigName >|  
|ErrNoValidInputFilesSpecified|Žádné platné vstupní soubory zadané. Zadejte buď dokumenty metadat, nebo soubory sestavení.|  
|ParametersLanguage|\<jazyk >|  
|ErrUnableToLoadMetadataDocument|Došlo k chybě při načítání metadat z jednoho načíst dokumentů. Je zadán identifikátor dokumentu.|  
|ErrConflictingInputs|Pro zadané vstupní argument v konfliktu s zadat, protože jejich implikují různé režimy činnosti nástroje.|  
|WrnUnableToLoadContractForValidation|Došlo k chybě při načítání typu kontraktu. Typ a podrobnosti nejsou zadány.|  
|WrnAttributeReflectionErrors|Atribut reflexe se nezdařilo pro některé typy v sestavení, které byly načteny z určeného. Ověřte, že z tohoto umístění s oprávněními správné zabezpečení mohou být načíst toto sestavení.|  
|HelpMetadataExportCategory|-= EXPORT METADAT =-|  
|HelpValidationCategory|-= OVĚŘENÍ SLUŽBY =-|  
|ValidationError|Chyba ověřování:|  
|GeneratingFiles|Generování souborů...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|Zadané možnosti byla předána neplatná hodnota. Zadaný cílový obor názvů nelze mapovat na více oborů názvů CLR jako zadaný.|  
|ErrCouldNotLoadReferenceAssemblyAt|Zadaný odkaz na sestavení nelze načíst.|  
|ParametersOut|\<Soubor >|  
|NoCodeWasGeneratedSuggestDCOnly|Generovat kontrakty z schémat, použijte Zadaná možnost.|  
|ErrUnableToLoadInputConfig|Zadaný konfigurační soubor nelze načíst.|  
|ErrUnexpectedDelimiter|Argument je neplatný oddělovač (': ' nebo '=') nelze spustit možnost.|  
|ErrMergeConfigUsedWithoutConfig|Zadaná možnost nelze použít bez zadání Zadaná možnost.|  
|ErrUnableToExportContract|Export kontrakt načíst ze zadaného typu došlo k chybě.|  
|GeneratingMetadata|Generování metadat souborů...|  
|ErrNotCodeDomType|Zadaný typ, který byl předán zadaný argument není zadaný odvozené třídy.|  
|WrnNoTypeForServices|Žádná z sestavení, které byly předány obsažené služby typů s názvem zadanou konfiguraci.|  
|ErrAssemblyLoadFailed|Zadaný soubor nelze načíst sestavení. Zkontrolujte FusionLogs Další informace.|  
|NoMetadataWasGenerated|Byly vygenerovány žádné soubory metadat. Žádné kontraktů služby byly exportovány.<br /><br /> Pokud chcete exportovat služby, použijte Zadaná možnost. Pokud chcete exportovat kontrakty dat, zadejte možnost.|  
|WrnCannotResolveServiceForExport|Nelze načíst službu s zadaný configName. Pokud chcete exportovat služby, zadejte sestavení, které obsahuje typ služby a spustitelný soubor s konfigurací pro tuto službu.|  
|ParametersCollectionType|\<Typ >|  
|ErrOptionConflictsWithTarget|Použití Zadaná možnost nepodporuje Zadaná možnost nastavit na zadanou hodnotu.|  
|ErrCodegenError|Došlo k chybě při generování kódu v daném jazyce.<br /><br /> Jazyk nepodporuje všechny elementy kódu probíhá generování. Je třeba použít jiný jazyk.|  
|ErrInputWsdlParseError|Při analýze WSDL došlo k chybě při čtení zadaného. Ověřte, že zadaný kód XML ve správném formátu a platné.|  
|ErrCouldNotCreateInstance|Nelze vytvořit instanci zadaného typu, který byl předán do zadaného argumentu.|  
|ParametersNamespace|\<řetězec, řetězec >|  
|HelpNostdlib|Neodkazují na standardní knihovny (ve výchozím nastavení mscorlib.dll a system.servicemodel.dll odkazují.)|  
|WrnCannotLoadConfigFileForExport|Došlo k chybě při zpracování konfiguračního souboru, který byl načten z určeného. Služby, které jsou definovány v tento konfigurační soubor nelze načíst.|  
|WrnUnableToLoadContractForExport|Došlo k chybě při načítání typu kontraktu. Nelze exportovat tento zadaného typu.|
