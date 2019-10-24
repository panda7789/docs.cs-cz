---
title: Nástroje
ms.date: 03/30/2017
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
ms.openlocfilehash: 623ba8a3ae3b58381edc80a19bf2d1a4561f3976
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774243"
---
# <a name="tools"></a>Nástroje
Toto téma obsahuje seznam všech výjimek generovaných nástroji Windows Communication Foundation (WCF).

## <a name="exception-list"></a>Seznam výjimek

|Kód prostředku|Řetězec prostředku|
|-------------------|---------------------|
|ParametersTarget|\<enum >|
|ParametersToolConfig|\<configFile >|
|ErrInvalidPath|Zadaná cesta je neplatná. Ověřte zadaný argument.|
|ParametersReference|\<file cesta >|
|WrnCannotLoadConfigFileForValidation|Při zpracování konfiguračního souboru načteného ze zadaného umístění došlo k chybě. Služby, které jsou definovány v tomto konfiguračním souboru, nelze ověřit.|
|MoreHelp|Pro další nápovědu zadejte "Svcutil" se zadanými argumenty.|
|HelpMergeConfig|Způsobí, že vygenerovaná konfigurace se sloučí do existujícího souboru místo přepsání stávajícího souboru.|
|ErrCannotWriteFile|Do výstupního souboru se nedá zapisovat.|
|ErrInvalidNamespaceArgument|Zadanou neplatnou hodnotu se předaly zadané možnosti. Zadejte čárkami oddělený cílový obor názvů a dvojici oborů názvů CLR.|
|HelpImportXmlType|Nakonfiguruje serializátor kontraktu DataContract pro import typů, které nejsou typu DataContract, jako typy IXmlSerializable.|
|ErrExclusiveOptionsSpecified|Zadanou možnost nelze použít, je-li zadána jiná zadaná možnost.|
|WrnHttpGetFailed|Chyba HTTP GET se zadaným identifikátorem URI.|
|ErrInputFileNotAssemblyOrMetadata|Soubor v zadaném umístění načtený přes zadaný vstupní argument se nezdá být souborem XML metadat ani platným sestavením.|
|WrnUnknownMetadataFound|Nelze uložit nerozpoznaný dokument metadat zadaného typu.|
|ErrDirectoryContainsInvalidCharacters|Zadanou neplatnou hodnotu se předaly zadané možnosti. Zadaný znak není v cestě povolený.|
|WrnCannotResolveServiceForValidation|Nepovedlo se načíst službu se zadaným parametrem config. Chcete-li ověřit službu, zadejte sestavení, které obsahuje typ služby a spustitelný soubor s konfigurací této služby.|
|ErrUnexpectedValue|Zadaná možnost nepodporuje žádné hodnoty.|
|#InvalidArg|Zadaný parametr obsahuje neplatný argument.|
|ParametersExcludeType|\<type >|
|HelpXmlSerializer|Vygenerujte datové typy, které používají XmlSerializer pro serializaci a deserializaci.|
|#|---------------------------------------------------------------------------------------------------------------------=|
|ErrUnexpectedError|V nástroji došlo k chybě.|
|HelpNologo|Zpráva o autorských právech a bannerech se potlačí.|
|ErrInputConflictsWithTarget|Typ vstupu načtený ze zadaného není podporován zadanou možností nastavenou na zadanou hodnotu.|
|WrnCannotLoadServiceForExport|Při načítání typu služby k exportu došlo k chybě.|
|HelpMetadataDownloadCategory|-= STAŽENÍ METADAT =-|
|WrnNoServiceContractTypes|Pro zadané sestavení nelze generovat typy XmlSerializer. Nenašly se žádné typy kontraktů služeb.|
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Při načítání typů do sestavení, které bylo načteno ze zadaného, došlo k chybě. Některé typy v sestavení nelze načíst a nejsou k dispozici pro nástroj.|
|ErrDirectoryPointsToAFile|Zadanou neplatnou hodnotu se předaly zadané možnosti. Zadaná hodnota je cesta k souboru.|
|Chyba|Chyba|
|ErrDuplicateReferenceValues|Zadané sestavení bylo načteno dvakrát pomocí zadané možnosti. Na sestavení může odkazovat pouze jednou.|
|WrnNoXmlSerializerOperationBehavior|Nelze vygenerovat XmlSerializer pro zadané sestavení. Žádný kontrakt služby v sestavení nemá operaci s XmlSerializerOperationBehavior.|
|ErrCannotCreateDirectory|Zadaný adresář nelze vytvořit.|
|ErrCouldNotLoadTypesFromAssemblyAt|Nelze načíst žádné typy v zadaném sestavení.|
|ErrUnknownSwitch|Zadaný přepínač je nerozpoznanou možností.|
|Symbol|Logo tohoto nástroje je "nástroj Microsoft® Service Model Metadata Tool" s verzí.|
|NoCodeWasGenerated|Nebyl vygenerován žádný kód.<br /><br /> Pokud jste se pokusili vygenerovat klienta, může to být způsobeno tím, že dokumenty metadat neobsahovaly žádné platné smlouvy ani služby.<br /><br /> nebo vzhledem k tomu, že všechny smlouvy nebo služby byly zjištěny v referenčních sestaveních. Ověřte, že jste do nástroje předali všechny dokumenty metadat.|
|WrnUnableToLoadContractForSGen|Při načítání typu kontraktu došlo k chybě. Pro tuto kontrakt nelze generovat typ XmlSerializer. Je určen typ a podrobnosti.|
|WrnOptionConflictsWithInput|Zadanou možnost nelze použít s více vstupními sestaveními. Zadaná možnost je ignorována.|
|ErrUnableToImportMetadata|Při pokusu o import metadat došlo ke kritické chybě.|
|ErrInvalidSerializer|Zadané možnosti byla předána neplatná hodnota serializátoru. Jsou zadány podporované serializátory.|
|SavingDownloadedMetadata|Ukládají se stažené soubory metadat...|
|WrnNoConfigForServices|Žádné z předaných sestavení nebylo spustitelné soubory s konfiguračním souborem nebo žádný z konfiguračních souborů, které obsahují služby se zadaným názvem konfigurace.|
|ErrInputConflictsWithOption|Vstup přečtený ze zadaného nelze použít se zadanou možností, protože předpokládá různé režimy fungování nástroje.|
|ErrUnableToExportEndpoints|Při exportování zadaného typu služby došlo k chybě.|
|ErrInputSchemaParseError|Při čtení zadaného souboru došlo k chybě analýzy schématu XML. Ověřte, že kód XML má správný formát a je platný.|
|ErrInputPolicyParseError|Při čtení zadaného typu došlo k chybě analýzy WS-Policy. Ověřte, že kód XML má správný formát a je platný.|
|ErrUnableToLoadReferenceType|Při načítání odkazovaného typu kontraktu došlo k chybě. Tento zadaný typ je ignorován.|
|WrnCannotLoadServiceForValidation|Při načítání služby k ověření došlo k chybě. Je určen typ a podrobnosti.|
|HelpCodeGenerationCategory|-= GENEROVÁNÍ KÓDU =-|
|RetreivingMetadataWithMexAndDisco|Probíhá pokus o stažení metadat ze zadaného WS-Metadata Exchange nebo DISCového systému.|
|ErrGeneralSchemaValidation|Při ověřování schémat XML vygenerovaných během exportu došlo k chybě.|
|ParametersDirectory|\<directory >|
|ErrCannotLoadSpecifiedType|Pro zadanou hodnotu, která byla předána zadané možnosti, nelze načíst žádný typ. Ujistěte se, že sestavení, k němuž tento typ patří, je zadáno pomocí zadané možnosti.|
|ErrOptionModeConflict|Zadanou možnost nelze použít se zadanou možností, protože implikují různé typy výstupu.|
|ErrIsNotAnAssembly|Nelze načíst zadaný jako sestavení. Ověřte, že tento soubor je sestavení .NET.|
|ErrInputConflictsWithMode|Vstup přečtený ze zadaného je nekonzistentní s jinými možnostmi.|
|ErrDuplicateValuePassedToTypeArg|Zadaná hodnota byla několikrát předána do zadané možnosti. Každý typ lze zadat pouze jednou.|
|ErrInputEPRFileParseError|Nejde přečíst odkaz na koncový bod ze zadaného. Ověřte, že kód XML má správný formát a je platný.|
|ErrCouldNotCreateCodeProvider|Pro zadanou hodnotu, která byla předána argumentu/{1}, nelze vytvořit poskytovatele kódu. Ověřte, že poskytovatel kódu je správně nainstalován a nakonfigurován.|
|ErrPathTooLongDirOnly|Výsledná zadaná cesta je příliš dlouhá. Zkontrolujte zadaný argument.|
|HelpDataContractSerializer|Vygenerujte datové typy, které používají serializátor DataContract pro serializaci a deserializaci.|
|ErrUnableToExportEndpoint|Došlo k chybě při exportování zadaného názvu koncového bodu v zadaném oboru názvů v zadaném typu služby, který byl nalezen v konfiguračním souboru načteném pro sestavení.|
|HelpUsage1|Zobrazí nápovědu k použití.|
|HelpUsage2|Zobrazí nápovědu k použití.|
|HelpUsage3|Zobrazí nápovědu k použití.|
|HelpUsage4|Zobrazí nápovědu k použití.|
|HelpUsage5|Zobrazí nápovědu k použití.|
|ErrDirectoryNotFound|Zadaný adresář nebyl nalezen. Ověřte, zda adresář existuje a zda máte příslušná oprávnění k jeho čtení.|
|ErrUnableToLoadFile|Zadaný soubor nelze číst.|
|ErrNoFilesFound|V zadané vstupní cestě se neodkazuje na žádný existující soubor.|
|ParametersConfig|\<configFile >|
|ErrDirectoryInsteadOfFile|Zadaná vstupní cesta se může jednat o adresář. Vstup musí být buď adresy URL, nebo cesty k souborům.|
|HelpConfig|Instruuje nástroje, aby vygenerovaly konfigurační soubor se zadaným názvem. Výchozí: Output. config.|
|ErrSingleUseSwitch|Zadanou možnost nelze zadat vícekrát.|
|Upozornění|Upozornění:|
|WrnAmbiguousServiceConfig|Bylo nalezeno více konfigurací služby se zadaným názvem konfigurace, jsou zadána následující sestavení.|
|ErrInvalidInputPath|Zadaná vstupní cesta neodkazuje na žádný existující soubor a zdá se, že se nejedná o platný identifikátor URI.|
|ErrUnableToLoadInputs|Při čtení načtených metadat došlo k chybě.|
|GeneratingSerializer|Generují se serializátory XML...|
|HelpToolConfig|Vlastní konfigurační soubor, který se má použít místo konfiguračního souboru aplikace. Dá se použít ke změně konfigurace metadat nebo registraci rozšíření konfigurace bez změny konfiguračního souboru nástroje.|
|ErrValidateInvalidUse|Zadanou možnost nelze použít se zadanou možností.|
|WrnWSMExFailed|WS-Metadata Exchange chyba se zadaným identifikátorem URI.|
|HelpNoconfig|Negenerovat konfiguraci.|
|HelpCodeGenerationDescription|Zadaná možnost může generovat kontrakty služby, klienty a datové typy z dokumentů metadat.|
|HelpTargetMetadata|Výstupní metadata Pokud je vstupem adresa URL, Svcutil. exe uloží metadata na disk a negeneruje kód. Pokud je vstupem jedno nebo více sestavení, Svcutil. exe generuje metadata z typů v sestaveních.|
|ErrAmbiguousOptionModeConflict|Zadaná možnost je v konfliktu s jinými možnostmi. Zkontrolujte použití nástroje.|
|ErrNotLanguageOrCodeDomType|Zadaná hodnota, která byla předána určenému argumentu, nepředstavuje definovaný jazyk a nelze ji načíst jako plně kvalifikovaný typ CLR.|
|ErrUnableToUniquifyFilename|Nelze vytvořit název výstupního souboru. Vytváří se příliš mnoho souborů se zadanou předponou.|
|ErrCannotCreateFile|Zadaný výstupní soubor nelze vytvořit.|
|ErrExpectedValue|Zadaná možnost vyžaduje, aby byla zadána hodnota.|
|ErrCannotDisambiguateSpecifiedTypes|V sadě odkazovaných sestavení existuje více než jeden typ se stejným názvem. Pro rozlišení mezi zadanými typy pro zadanou možnost použijte názvy kvalifikované pro sestavení.|
|RetreivingMetadataWithMexOnly|Probíhá pokus o stažení metadat ze zadaného umístění pomocí WS-Metadata Exchange. Tato adresa URL nepodporuje DISCích.|
|ErrInvalidTarget|Zadaný cíl je neplatný, je-li zadán pomocí zadané možnosti. Jsou zadány podporované cíle.|
|ErrPathTooLong|Výsledná cesta je příliš dlouhá. Zkontrolujte zadané argumenty.|
|HelpCommonOptionsCategory|-= SPOLEČNÉ MOŽNOSTI =-|
|ParametersServiceName|\<serviceConfigName >|
|ErrNoValidInputFilesSpecified|Nebyly zadány žádné platné vstupní soubory. Zadejte buď dokumenty metadat, nebo soubory sestavení.|
|ParametersLanguage|\<language >|
|ErrUnableToLoadMetadataDocument|Při čtení metadat z jednoho načteného dokumentu došlo k chybě. Byl zadán identifikátor dokumentu.|
|ErrConflictingInputs|Zadaný vstupní argument je v konfliktu se zadaným vzhledem k tomu, že implikují různé režimy fungování nástroje.|
|WrnUnableToLoadContractForValidation|Při načítání typu kontraktu došlo k chybě. Je určen typ a podrobnosti.|
|WrnAttributeReflectionErrors|Pro některé typy v sestavení, které byly načteny ze zadaného, se odraz atributů nezdařil. Ověřte, že toto sestavení může být načteno z tohoto umístění se správnými oprávněními zabezpečení.|
|HelpMetadataExportCategory|-= EXPORT METADAT =-|
|HelpValidationCategory|-= OVĚŘENÍ SLUŽBY =-|
|ValidationError|Chyba ověřování:|
|GeneratingFiles|Generují se soubory...|
|ErrCannotSpecifyMultipleMappingsForNamespace|Zadané možnosti byla předána neplatná hodnota. Zadaný cílový obor názvů nelze namapovat na několik oborů názvů CLR, jak je uvedeno.|
|ErrCouldNotLoadReferenceAssemblyAt|Zadané referenční sestavení nelze načíst.|
|Parametry|\<file >|
|NoCodeWasGeneratedSuggestDCOnly|Pokud chcete vygenerovat smlouvy ze schémat, použijte určenou možnost.|
|ErrUnableToLoadInputConfig|Zadaný konfigurační soubor nelze načíst.|
|ErrUnexpectedDelimiter|Neplatný oddělovač argumentů (: nebo =) nemůže spustit možnost.|
|ErrMergeConfigUsedWithoutConfig|Nelze použít zadanou možnost bez zadání jiné zadané možnosti.|
|ErrUnableToExportContract|Při exportování kontraktu načteného ze zadaného typu došlo k chybě.|
|GeneratingMetadata|Generují se soubory metadat...|
|ErrNotCodeDomType|Zadaný typ, který byl předán zadanému argumentu, není určenou odvozenou třídou.|
|WrnNoTypeForServices|Žádná ze sestavení, která nebyla předána, obsahovala typy služeb se zadaným názvem konfigurace.|
|ErrAssemblyLoadFailed|Zadaný soubor nelze načíst jako sestavení. Další informace najdete v FusionLogs.|
|NoMetadataWasGenerated|Vygenerovaly se žádné soubory metadat. Nebyly vyexportovány žádné kontrakty služeb.<br /><br /> Chcete-li exportovat službu, použijte určenou možnost. Pokud chcete exportovat kontrakty dat, zadejte možnost.|
|WrnCannotResolveServiceForExport|Nepovedlo se načíst službu se zadaným parametrem config. Chcete-li exportovat službu, zadejte sestavení, které obsahuje typ služby a spustitelný soubor s konfigurací pro tuto službu.|
|ParametersCollectionType|\<type >|
|ErrOptionConflictsWithTarget|Použití zadané možnosti není podporováno se zadanou možností nastavenou na zadanou hodnotu.|
|ErrCodegenError|Při generování kódu v zadaném jazyce došlo k chybě.<br /><br /> Jazyk nepodporuje generování všech generovaných prvků kódu. Měl by se použít jiný jazyk.|
|ErrInputWsdlParseError|Při čtení zadaného prvku došlo k chybě analýzy WSDL. Ověřte, že kód XML má správný formát a je platný.|
|ErrCouldNotCreateInstance|Nelze vytvořit instanci zadaného typu, která byla předána zadanému argumentu.|
|ParametersNamespace|\<string, > řetězců|
|HelpNostdlib|Neodkazovat na standardní knihovny (ve výchozím nastavení jsou odkazovány knihovny mscorlib. dll a System. ServiceModel. dll)|
|WrnCannotLoadConfigFileForExport|Při zpracování konfiguračního souboru, který byl načten ze zadaného, došlo k chybě. Služby, které jsou definovány v tomto konfiguračním souboru, nelze načíst.|
|WrnUnableToLoadContractForExport|Při načítání typu kontraktu došlo k chybě. Tento zadaný typ nelze exportovat.|
