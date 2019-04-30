---
title: Metadata architektury služby
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f65f53ff99202275876fb6e3c431bc49ae2bd38b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780793"
---
# <a name="service-framework-metadata"></a>Metadata architektury služby
Toto téma uvádí všechny výjimky generované Metadata architektury služby.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód zdroje|Řetězec prostředku|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Asynchronní ukončení bylo voláno pro nesprávný kanál.|  
|AsyncEndCalledWithAnIAsyncResult|Asynchronní ukončení byla volána s argumentem IAsyncResult z jiné metody zahájení.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Byl proveden pokus získat typ kontraktu pro zadaný rozbočovač. Typ není ServiceContract a třídu ServiceContract nedědí.|  
|CannotHaveTwoOperationsWithTheSameName3|V jednom kontraktu se stejným názvem nemůžou být dvě operace. Toto pravidlo porušují určených metod v zadaném typu. Změňte název jedné z operací, že změníte název metody nebo použijete vlastnost Name atributu OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Nejde Zdědit dvě různé operace se stejným názvem. Toto pravidlo porušují zadanou operaci ze zadaného smluv. Změňte název jedné z operací, že změníte název metody nebo použijete vlastnost Name atributu OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Nelze vytvořit kanál pro kontrakt, který vyžaduje požadavek nebo odpověď a vazbu, která vyžaduje ruční adresování, ale podporuje pouze duplexní komunikaci.|  
|DuplicateBehavior1|Hodnotu nelze přidat do kolekce. Kolekce již obsahuje položku stejného zadaného typu. Tato kolekce podporuje pouze jednu instanci každého typu.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Zadané základní smlouvu obsahuje kontrakt zpětného volání zadané, a proto zadané odvozené servisní smlouvě musíte zadat také zadaného typu nebo odvozeného typu jako jeho kontrakt zpětného volání.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Neplatný asynchronní signatura metody Begin pro zadanou metodu v zadaném typu třídy ServiceContract. Vaše begin musí jako poslední dva argumenty přijímat ukazatel AsyncCallback a objekt a vracet hodnotu IAsyncResult metody.|  
|InvalidAsyncEndMethodSignatureForMethod2|Neplatný asynchronní signatura metody End pro zadanou metodu v zadaném typu třídy ServiceContract. Metoda end musí přijmout třídu IAsyncResult jako poslední argument.|  
|MessagePropertiesArraySize0|Pole, který byl předán nemá dostatek prostoru k udržení všech vlastností obsažených v této kolekci.|  
|OneWayAndFaultsIncompatible2|Zadanou metodu v zadaném typu je označená jako IsOneWay = true a deklaruje jednu nebo víc tříd FaultContractAttributes. Jednosměrné metody nemůžou deklarovat třídu FaultContractAttributes. Změňte IsOneWay na false nebo odstraňte FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Nepodporovaná Web Services Description Language. Pro chybové zprávy je podporována pouze jedna část zprávy. Tato chybová zpráva se odkazuje na více než jednu část zprávy. Pokud máte přístup pro úpravy k souboru popisu webové služby, můžete problém vyřešit odstraněním dodatečných částí zprávy takový, aby chybová zpráva odkazy pouze na jednu část.|  
|UnsupportedWSDLTheFault|Nepodporovaná Web Services Description Language. Část chybové zprávy musí odkazovat na prvek. Tato chybová zpráva neodkazuje na element. Pokud máte přístup pro úpravy dokumentu jazyka pro definici webové služby, můžete opravit problém pomocí odkazu na element schématu pomocí atributu "element".|  
|WsdlImportErrorDependencyDetail|Došlo k chybě při importu zadané, že je závislé na zadanou hodnotu. Cesta Xpath je také zadán.|  
|XsdMissingRequiredAttribute1|Zadaný chybí požadovaný atribut.|
