---
title: Metadata architektury služby
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f3e73df54b3389b2c9f27001953be147b27eb6f8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991206"
---
# <a name="service-framework-metadata"></a>Metadata architektury služby
Toto téma obsahuje seznam všech výjimek generovaných metadaty rozhraní Service Framework.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|V nesprávném kanálu byl volán asynchronní konec.|  
|AsyncEndCalledWithAnIAsyncResult|Asynchronní ukončení bylo voláno s objektem IAsyncResult z jiné metody begin.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Byl proveden pokus o získání typu kontraktu pro zadaný typ. Typ není ServiceContract a nedědí třídu ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Nelze mít dvě operace ve stejné kontraktu se stejným názvem. Zadané metody v zadaném typu porušují toto pravidlo. Změnou názvu metody nebo pomocí vlastnosti Name atributu OperationContractAttribute změňte název jedné z operací.|  
|CannotInheritTwoOperationsWithTheSameName3|Nelze zdědit dvě různé operace se stejným názvem. Zadaná operace ze zadaných kontraktů porušuje toto pravidlo. Změnou názvu metody nebo pomocí vlastnosti Name atributu OperationContractAttribute změňte název jedné z operací.|  
|CantCreateChannelWithManualAddressing|Nelze vytvořit kanál pro kontrakt, který vyžaduje požadavek nebo odpověď a vazbu, která vyžaduje ruční adresování, ale podporuje pouze duplexní komunikaci.|  
|DuplicateBehavior1|Hodnotu nelze přidat do kolekce. Kolekce již obsahuje položku stejného zadaného typu. Tato kolekce podporuje pouze jednu instanci každého typu.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Vzhledem k tomu, že zadaný kontrakt základní služby má zadanou smlouvu zpětného volání, zadaný odvozený kontrakt služby musí také zadat buď zadaný typ, nebo odvozený typ jako svůj kontrakt zpětného volání.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Neplatná signatura asynchronní metody begin pro zadanou metodu v zadaném typu třídy ServiceContract. Metoda Begin musí jako poslední dva argumenty přijmout AsyncCallback a Object a vracet IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Neplatná signatura asynchronní metody end pro zadanou metodu v zadaném typu třídy ServiceContract. Vaše metoda end musí převzít rozhraní IAsyncResult jako poslední argument.|  
|MessagePropertiesArraySize0|Předané pole nemá dostatek místa pro uložení všech vlastností obsažených v této kolekci.|  
|OneWayAndFaultsIncompatible2|Zadaná metoda v zadaném typu je označena jako IsOneWay = true a deklaruje jednu nebo více FaultContractAttributes. Jednosměrné metody nemohou deklarovat FaultContractAttributes. Změňte IsOneWay na false nebo odeberte FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Nepodporovaný jazyk popisu webové služby Pro chybové zprávy je podporována pouze jedna část zprávy. Tato chybová zpráva odkazuje na více než jednu část zprávy. Máte-li přístup pro úpravy k souboru jazyka popisu webové služby, můžete tento problém vyřešit odebráním dalších částí zpráv, které chybové zprávy odkazují pouze na jednu část.|  
|UnsupportedWSDLTheFault|Nepodporovaný jazyk popisu webové služby Část chybové zprávy musí odkazovat na element. Tato chybová zpráva neodkazuje na element. Máte-li přístup pro úpravy k dokumentu definice Web Services, můžete problém vyřešit tak, že na element schématu odkazujete pomocí atributu ' element '.|  
|WsdlImportErrorDependencyDetail|Při importu zadaného, na kterém je závislá jiná zadaná hodnota, došlo k chybě. Cesta XPath je také určena.|  
|XsdMissingRequiredAttribute1|Chybí zadaný požadovaný atribut.|
