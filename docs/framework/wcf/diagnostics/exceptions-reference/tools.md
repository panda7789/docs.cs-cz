---
title: Nástroje
ms.date: 03/30/2017
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
ms.openlocfilehash: 6c4ada74c2fc6aba84eb1fe46f4d7cdee9978d13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780741"
---
# <a name="tools"></a>Nástroje
Toto téma uvádí všechny výjimky generované nástroje Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|ParametersTarget|\<enum>|  
|ParametersToolConfig|\<configFile>|  
|ErrInvalidPath|Zadané je neplatnou cestu. Zkontrolujte zadaný argument.|  
|ParametersReference|\<Cesta k souboru >|  
|WrnCannotLoadConfigFileForValidation|Došlo k chybě při zpracování konfiguračního souboru načtených ze zadaného umístění. Služby, které jsou definovány v tento konfigurační soubor nejde ověřit.|  
|MoreHelp|Další nápovědu zadejte svcutil / "se zadanými argumenty.|  
|HelpMergeConfig|Způsobí, že vygenerovanou konfiguraci ke sloučení do existujícího souboru namísto přepsání existujícího souboru.|  
|ErrCannotWriteFile|Nelze zapisovat do výstupního souboru.|  
|ErrInvalidNamespaceArgument|Zadaná možnost byl předán zadaná neplatná hodnota. Zadejte čárkami cílový obor názvů a pár oboru názvů CLR.|  
|HelpImportXmlType|Nakonfiguruje serializátor kontraktu dat DataContract pro import typy jiné než DataContract jako IXmlSerializable typy.|  
|ErrExclusiveOptionsSpecified|Zadaná možnost nelze použít, pokud zadaná možnost jste zadali.|  
|WrnHttpGetFailed|Chyba protokolu HTTP GET s zadaný identifikátor URI.|  
|ErrInputFileNotAssemblyOrMetadata|Soubor v zadaném umístění přečtený pomocí argumentu zadaný vstupní soubor metadat XML nebo platné sestavení nezobrazí.|  
|WrnUnknownMetadataFound|Nerozpoznaná metadata dokument zadaného typu nelze uložit.|  
|ErrDirectoryContainsInvalidCharacters|Zadaná možnost byl předán zadaná neplatná hodnota. Zadaný znak není v cestě povolen.|  
|WrnCannotResolveServiceForValidation|Nepovedlo se načíst služby se zadaným configName. K ověření služby, zadejte oba sestavení obsahující typ služby a spustitelný soubor s konfigurací pro tuto službu.|  
|ErrUnexpectedValue|Zadaná možnost nepodporuje žádné hodnoty.|  
|#InvalidArg|Zadaný obsahuje neplatný argument.|  
|ParametersExcludeType|\<Typ >|  
|HelpXmlSerializer|Generování datových typů, které k serializaci a deserializaci používají XmlSerializer.|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|V nástroji došlo k chybě.|  
|HelpNologo|Zprávu o autorských právech a úvodní nápis je potlačeno.|  
|ErrInputConflictsWithTarget|Přečtená vstupní data ze zadaného typu se nepodporuje s Zadaná možnost nastavit na zadanou hodnotu.|  
|WrnCannotLoadServiceForExport|Došlo k chybě při načítání typu služby nelze exportovat.|  
|HelpMetadataDownloadCategory|-= STAŽENÍ METADAT =-|  
|WrnNoServiceContractTypes|Pro zadané sestavení nelze vygenerovat typy XmlSerializer. Nenašly se žádné typy kontraktu služby.|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Došlo k chybě při načítání typů v sestavení, která byla načtena ze zadané. Některé typy v sestavení nelze načíst a nejsou k dispozici pro nástroj.|  
|ErrDirectoryPointsToAFile|Zadaná možnost byl předán zadaná neplatná hodnota. Zadaná hodnota je cesta k souboru.|  
|Chyba|Chyba:|  
|ErrDuplicateReferenceValues|Zadané sestavení bylo načteno dvakrát pomocí zadané možnosti. Pouze odkaz na sestavení lze jednou.|  
|WrnNoXmlSerializerOperationBehavior|Pro zadané sestavení nelze vygenerovat třídy XmlSerializer. Žádný kontrakt služby v sestavení nemá operaci s XmlSerializerOperationBehavior.|  
|ErrCannotCreateDirectory|Zadaný adresář nelze vytvořit.|  
|ErrCouldNotLoadTypesFromAssemblyAt|Nelze načíst žádné typy v zadaném sestavení.|  
|ErrUnknownSwitch|Zadaný přepínač je nerozpoznanou možnost.|  
|Logo|Logo nástroje je "Nástroj Microsoft® Service Model metadat" s verzí.|  
|NoCodeWasGenerated|Nevygeneroval se žádný kód.<br /><br /> Pokud jste se pokoušeli vygenerovat klienta, to může být, že dokumenty metadat neobsahovaly žádné platné kontrakty ani služby<br /><br /> nebo protože bylo zjištěno, že všechny kontrakty nebo služby existují v sestaveních reference. Ověřte, že jste nástroji předali všechny dokumenty metadat.|  
|WrnUnableToLoadContractForSGen|Došlo k chybě při načítání typu kontraktu. Nejde generovat typ XmlSerializer pro tento kontrakt. Typ a podrobnosti jsou uvedeny.|  
|WrnOptionConflictsWithInput|Zadaná možnost nelze použít s více vstupních sestaveních. Zadaná možnost se ignoruje.|  
|ErrUnableToImportMetadata|Došlo ke kritické chybě při pokusu o import metadat.|  
|ErrInvalidSerializer|Zadaná možnost byl předán neplatná hodnota serializátoru. Podporované serializátory nejsou zadány.|  
|SavingDownloadedMetadata|Ukládání souborů stažené metadata...|  
|WrnNoConfigForServices|Nebyly žádné sestavení předané spustitelné soubory s konfiguračním souboru nebo žádný konfigurační soubory obsažené služby s názvem zadanou konfiguraci.|  
|ErrInputConflictsWithOption|Vstup přečtený z určeného nelze použít s parametrem zadané, protože implikují různé režimy fungování nástroje.|  
|ErrUnableToExportEndpoints|Při exportu zadaný typ služby došlo k chybě.|  
|ErrInputSchemaParseError|Chyba parsování schématu XML došlo k chybě při čtení zadaného. Ověřte, kód XML má správný formát a je platný.|  
|ErrInputPolicyParseError|Při čtení zadaného došlo k chybě parsování WS-Policy. Ověřte, kód XML má správný formát a je platný.|  
|ErrUnableToLoadReferenceType|Došlo k chybě při načítání typu odkazovaného kontraktu. Tato zadaného typu se ignoruje.|  
|WrnCannotLoadServiceForValidation|Došlo k chybě při načítání služby má být ověřen. Typ a podrobnosti jsou uvedeny.|  
|HelpCodeGenerationCategory|-= GENEROVÁNÍ KÓDU =-|  
|RetreivingMetadataWithMexAndDisco|Pokus o stažení metadat z určeného pomocí protokolu WS-Metadata Exchange nebo roz.|  
|ErrGeneralSchemaValidation|Při ověřování schémat XML generovaných při exportu došlo k chybě.|  
|ParametersDirectory|\<directory>|  
|ErrCannotLoadSpecifiedType|Pro zadanou hodnotu, která byla předána Zadaná možnost je možné načíst žádný typ. Ujistěte se, že sestavení, které patří tento typ je určen pomocí Zadaná možnost.|  
|ErrOptionModeConflict|Zadaná možnost nelze použít s parametrem zadané, protože tyto možnosti implikují různé typy výstupu.|  
|ErrIsNotAnAssembly|Nelze načíst zadané sestavení. Ověřte, že tento soubor sestavení .NET.|  
|ErrInputConflictsWithMode|Vstup přečtený z určeného není konzistentní s jinými možnostmi.|  
|ErrDuplicateValuePassedToTypeArg|Zadaná hodnota byl předán Zadaná možnost více než jednou. Každý typ lze zadat pouze jednou.|  
|ErrInputEPRFileParseError|Nelze přečíst odkaz koncového bodu z určeného. Ověřte, kód XML má správný formát a je platný.|  
|ErrCouldNotCreateCodeProvider|Pro zadanou hodnotu, která byla předána nemůže vytvořit poskytovatele kódu /{1} argument. Ověřte, že poskytovatel kódu je správně nainstalován a nakonfigurován.|  
|ErrPathTooLongDirOnly|Výsledná zadaná cesta je příliš dlouhý. Zkontrolujte zadaný argument.|  
|HelpDataContractSerializer|Generování datových typů, které k serializaci a deserializaci používají serializátor kontraktu dat DataContract.|  
|ErrUnableToExportEndpoint|Při exportu názvu zadaný koncový bod v určeném oboru názvů v zadaný typ služby nalezena v konfiguračním souboru pro sestavení načíst. došlo k chybě.|  
|HelpUsage1|Zobrazí nápovědu využití.|  
|HelpUsage2|Zobrazí nápovědu využití.|  
|HelpUsage3|Zobrazí nápovědu využití.|  
|HelpUsage4|Zobrazí nápovědu využití.|  
|HelpUsage5|Zobrazí nápovědu využití.|  
|ErrDirectoryNotFound|Zadaný adresář se nenašel. Ověřte, že adresář existuje a zda máte příslušná oprávnění k jeho čtení.|  
|ErrUnableToLoadFile|Zadaný soubor nelze číst.|  
|ErrNoFilesFound|Zadaný vstupní cesta neodkazuje na žádný existující soubor nezobrazí.|  
|ParametersConfig|\<configFile>|  
|ErrDirectoryInsteadOfFile|Zadaný vstupní cesta se zdá být adresář. Vstup musí být buď adresy URL, nebo cesty k souborům.|  
|HelpConfig|Dává pokyn nástroji, abyste mohli vygenerovat konfigurační soubor se zadaným názvem. Výchozí: output.config.|  
|ErrSingleUseSwitch|Zadaná možnost nelze zadat více než jednou.|  
|Upozornění|Upozornění:|  
|WrnAmbiguousServiceConfig|Více konfigurací služby nebyly nalezeny s názvem zadanou konfiguraci, jsou specifikovány následující sestavení.|  
|ErrInvalidInputPath|Zadaný vstupní cesta neodkazuje na žádný existující soubor se nezobrazí a zřejmě není platným identifikátorem URI.|  
|ErrUnableToLoadInputs|Během čtení načtených metadat došlo k chybě.|  
|GeneratingSerializer|Generuje se serializátory XML...|  
|HelpToolConfig|Vlastní konfigurační soubor oznamujícím konfiguračního souboru aplikace. To umožňuje změnit konfiguraci metadat nebo registraci rozšíření konfigurace beze změny konfiguračního souboru nástroje.|  
|ErrValidateInvalidUse|Zadaná možnost nelze použít s parametrem zadané.|  
|WrnWSMExFailed|Chyba WS-Metadata Exchange se zadaným identifikátorem URI.|  
|HelpNoconfig|Konfiguraci nelze vytvořit.|  
|HelpCodeGenerationDescription|Zadaný seznam můžete vygenerovat typy kontraktů, klientů a dat služby z dokumentů metadat.|  
|HelpTargetMetadata|Výstupní metadata. Pokud je vstup adresu URL, Svcutil.exe uloží metadata na disk a nevygeneruje žádný kód. Pokud je vstup jednu nebo více sestavení, vygeneruje Svcutil.exe metadat z typů v sestaveních.|  
|ErrAmbiguousOptionModeConflict|Zadaná možnost je v konfliktu s jinými možnostmi. Zkontrolujte způsob použití nástroje.|  
|ErrNotLanguageOrCodeDomType|Zadaná hodnota, která byla předána zadaného argumentu nepředstavuje definovaný jazyk a nelze jej načíst jako plně kvalifikovaný typ CLR.|  
|ErrUnableToUniquifyFilename|Nelze vytvořit název výstupního souboru. Příliš mnoho souborů jsou vytvářeny pomocí zadané předpony.|  
|ErrCannotCreateFile|Zadaný výstupní soubor nelze vytvořit.|  
|ErrExpectedValue|Zadaná možnost vyžaduje, aby byl specifikován hodnotu.|  
|ErrCannotDisambiguateSpecifiedTypes|V sadě odkazovaných sestavení existuje více než jeden typ se stejným názvem. Úplné názvy sestavení použijte k rozlišení mezi zadanými typy pro zadanou možnost.|  
|RetreivingMetadataWithMexOnly|Došlo k pokusu o stažení metadat ze zadaného umístění pomocí protokolu WS-Metadata Exchange. Tato adresa URL nepodporuje roz.|  
|ErrInvalidTarget|Zadaný cíl je platný, pokud je určen pomocí Zadaná možnost. Cíle, které podporované nejsou zadány.|  
|ErrPathTooLong|Výsledná cesta je příliš dlouhý. Zkontrolujte zadané argumenty.|  
|HelpCommonOptionsCategory|-= SPOLEČNÉ MOŽNOSTI =-|  
|ParametersServiceName|\<serviceConfigName>|  
|ErrNoValidInputFilesSpecified|Platný zadány žádné vstupní soubory. Zadejte buď dokumentů metadat nebo soubory sestavení.|  
|ParametersLanguage|\<jazyk >|  
|ErrUnableToLoadMetadataDocument|Při čtení metadat z jednoho z načtených dokumentů došlo k chybě. Je zadaný identifikátor dokumentu.|  
|ErrConflictingInputs|Zadaný vstupní argument je v konfliktu s zadat, protože implikují různé režimy fungování nástroje.|  
|WrnUnableToLoadContractForValidation|Došlo k chybě při načítání typu kontraktu. Typ a podrobnosti jsou uvedeny.|  
|WrnAttributeReflectionErrors|Atribut reflexe se nezdařilo pro některý z typů v sestavení, která byla načtena ze zadané. Ověřte, že toto sestavení lze načíst z tohoto umístění s oprávněními správné zabezpečení.|  
|HelpMetadataExportCategory|-= EXPORT METADAT =-|  
|HelpValidationCategory|-= OVĚŘENÍ SLUŽBY =-|  
|ValidationError|Chyba ověřování:|  
|GeneratingFiles|Generují se soubory...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|Zadaná nastavení byla předána neplatná hodnota. Zadaný cílový obor názvů nejde mapovat na více oborů názvů CLR uvedená.|  
|ErrCouldNotLoadReferenceAssemblyAt|Zadaný odkaz sestavení nelze načíst.|  
|ParametersOut|\<Soubor >|  
|NoCodeWasGeneratedSuggestDCOnly|Chcete-li generovat kontrakty ze schémat, použijte Zadaná možnost.|  
|ErrUnableToLoadInputConfig|Nelze načíst zadaný konfigurační soubor.|  
|ErrUnexpectedDelimiter|Neplatný argument: oddělovač (': ' nebo '=') nemůže spustit možnost.|  
|ErrMergeConfigUsedWithoutConfig|Zadaná možnost nelze použít bez zadání Zadaná možnost.|  
|ErrUnableToExportContract|Došlo k chybě při exportu kontrakt načtených ze zadaného typu.|  
|GeneratingMetadata|Generování souborů metadat...|  
|ErrNotCodeDomType|Zadaný typ, který byl předán zadaný argument není zadaný odvozené třídy.|  
|WrnNoTypeForServices|Žádná sestavení, které byly předány omezením typů s názvem konfigurace služeb.|  
|ErrAssemblyLoadFailed|Zadaný soubor nelze načíst sestavení. Více informací naleznete FusionLogs.|  
|NoMetadataWasGenerated|Nevygenerovaly se žádné soubory metadat. Byly exportovány bez kontraktů služby.<br /><br /> Export služby, použijte parametr zadaný. Export dat smlouvy, zadejte možnost.|  
|WrnCannotResolveServiceForExport|Nepovedlo se načíst služby se zadaným configName. Export služby, zadejte sestavení, který obsahuje typ služby a spustitelný soubor s konfigurací pro tuto službu.|  
|ParametersCollectionType|\<Typ >|  
|ErrOptionConflictsWithTarget|Použití Zadaná možnost nepodporuje Zadaná možnost nastavit na zadanou hodnotu.|  
|ErrCodegenError|Při generování kódu v zadaném jazyce došlo k chybě.<br /><br /> Jazyk nepodporuje všechny generované elementy kódu. Je třeba použít jiný jazyk.|  
|ErrInputWsdlParseError|Chyba parsování WSDL došlo k chybě při čtení zadaného. Ověřte, kód XML má správný formát a je platný.|  
|ErrCouldNotCreateInstance|Nelze vytvořit instanci zadaného typu, který byl předán zadaného argumentu.|  
|ParametersNamespace|\<řetězec, řetězec >|  
|HelpNostdlib|Neodkazovat na standardní knihovny (ve výchozím nastavení mscorlib.dll a system.servicemodel.dll jsou odkazovány.)|  
|WrnCannotLoadConfigFileForExport|Došlo k chybě při zpracování konfiguračního souboru, který byl načten ze zadané. Služby, které jsou definovány v tento konfigurační soubor nelze načíst.|  
|WrnUnableToLoadContractForExport|Došlo k chybě při načítání typu kontraktu. Není možné exportovat tento zadaného typu.|
