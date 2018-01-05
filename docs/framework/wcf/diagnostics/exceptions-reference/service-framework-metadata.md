---
title: "Metadata architektury služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cab33ec4a3f3e42c4ec373073e171a7dcfeace2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-framework-metadata"></a>Metadata architektury služby
Toto téma uvádí všechny výjimky generované Metadata architektury služby.  
  
## <a name="exception-list"></a>Seznam výjimek  
  
|Kód prostředku|Řetězec prostředku|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Asynchronní End byla volána na chybný kanál.|  
|AsyncEndCalledWithAnIAsyncResult|Asynchronní End byla volána s IAsyncResult z jiné metody Begin.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Došlo k pokusu o získání pro zadaný typ smlouvy. Typ není třída ServiceContract a nedědí třída ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Nemůže mít dvě operace v stejné smlouvy se stejným názvem. Toto pravidlo porušují zadané metody v zadaného typu. Změňte název jednoho z operace změnou názvu metody nebo pomocí vlastnosti název OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Nelze zdědit dvě různé operace se stejným názvem. Zadaná operace ze zadaného smluv porušení toto pravidlo. Změňte název jednoho z operace změnou názvu metody nebo pomocí vlastnosti název OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Nelze vytvořit kanál pro kontrakt, který vyžaduje požadavek nebo odpověď a vazbu, která vyžaduje ruční adresování ale podporuje pouze duplexní komunikace.|  
|DuplicateBehavior1|Hodnotu nelze přidat do kolekce. Kolekce již obsahuje položku stejné zadaného typu. Tato kolekce podporuje pouze jednu instanci každého typu.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Protože kontrakt zadané základní služby má kontraktu zadaný zpětného volání, kontrakt služby zadaný odvozené také třeba určit buď zadaný typ, nebo odvozený typ jako její smlouvy zpětného volání.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Neplatný asynchronní Begin podpis metody pro zadanou metodu v zadaný typ ServiceContract. Vaše začít metoda musí přijmout třídu AsyncCallback a objekt jako poslední dva argumenty a vrátit třídu IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Neplatný asynchronní End podpis metody pro zadanou metodu v zadaný typ ServiceContract. Metoda ukončení musí přijmout třídu IAsyncResult jako poslední argument.|  
|MessagePropertiesArraySize0|Pole, který byl předán nemá dostatek místa pro uložení všech vlastností obsažených v této kolekci.|  
|OneWayAndFaultsIncompatible2|Zadanou metodu v zadaného typu, je označeno jako IsOneWay = true a deklaruje jednu nebo více tříd FaultContractAttributes. Jednosměrné metody nelze deklarovat FaultContractAttributes. Změnit IsOneWay na hodnotu false nebo odebrat třídu FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Nepodporované Web Services Description Language. Pro chybové zprávy je podporována pouze jedna část zprávy. Tato chybová zpráva se odkazuje na více než jednu část zprávy. Používáte-li upravit přístup k souboru popisu webové služby, můžete je vyřešit problém odebráním částí další zprávy, aby chybová zpráva odkazy pouze na jednu část.|  
|UnsupportedWSDLTheFault|Nepodporované Web Services Description Language. Část chybové zprávy musí odkazovat na prvek. Tato chybová zpráva není odkaz na element. Pokud máte přístup pro úpravy dokumentu webové služby Definition Language, můžete problém vyřešit pomocí odkazu na prvek schématu pomocí atributu 'element'.|  
|WsdlImportErrorDependencyDetail|Došlo k chybě při importu zadaný, je závislá na zadanou hodnotu. Rovněž je zadán argument Xpath.|  
|XsdMissingRequiredAttribute1|Chybí zadaný povinný atribut.|
