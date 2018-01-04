---
title: "Vytváření vlastních toku řízení aktivit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57c347043d1bbcf239841bc57c6a406cfc9af7f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-custom-flow-control-activities"></a>Vytváření vlastních toku řízení aktivit
.Net Framework obsahuje celou řadu řízení toku aktivity, které fungují podobně jako abstraktní programovací struktury (například <xref:System.Activities.Statements.Flowchart>) nebo se standardní programovací příkazy (například <xref:System.Activities.Statements.If>). Toto téma popisuje architekturu jednoho z ukázkových projektů [Non-obecné ForEach](../../../docs/framework/windows-workflow-foundation/samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Vytvoření vlastní třídy  
 Vzhledem k tomu, že ForEach Non-obecná třída bude třeba naplánovat podřízené aktivity, ji budou muset být odvozen z <xref:System.Activities.NativeActivity>, od aktivity, které jsou odvozeny od <xref:System.Workflow.Activities.CodeActivity> nemají tuto funkci.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 Vlastní třída vyžaduje několik členů k ukládání dat používá aktivitu a funkce spuštění aktivity podřízené aktivity. Tito členové patří:  
  
-   `valueEnumerator`: Neveřejný <xref:System.Activities.Variable%601> typu <xref:System.Collections.IEnumerator> použít pro iteraci prostřednictvím kolekce položek. Tento člen je typu <xref:System.Activities.Variable%601> vzhledem k tomu, že se používá interně v aktivity, nikoli argument nebo veřejné vlastnosti, který se použije, pokud se tento objekt tak, aby měl počátek mimo aktivity.  
  
-   `OnChildComplete`: Veřejné <xref:System.Activities.CompletionCallback> vlastnost, která spustí po dokončení provádění jednotlivých podřízených. Tento člen je definován jako vlastnost CLR, vzhledem k tomu, že nedojde ke změně jeho hodnota pro různé instance aktivity.  
  
-   `Values`: Kolekce vstupy používá pro opakování podřízené aktivity. Tento člen je typu <xref:System.Activities.InArgument%601>, protože je původu dat mimo aktivitu, ale obsah kolekce neočekává změnit během provádění aktivity. V případě potřeby funkce pro změnu obsahu této kolekce v průběhu provádění aktivity (Chcete-li přidat nebo odebrat aktivity, například) aktivity tento člen by byla definována jako <xref:System.Activities.ActivityAction>, které by byly vyhodnocovány pokaždé, když byl přistupoval, takže změny budou k dispozici pro aktivity.  
  
-   `Body`: Aktivitu nelze provést pro každou položku v definuje tento člen `Values` kolekce. Tento člen je definován jako <xref:System.Activities.ActivityAction> tak, aby vyhodnotí se pokaždé, když je přístupný.  
  
-   `Execute`: Tato metoda používá `InternalExecute`, `OnForEachComplete`, a `GetStateAndExecute` neveřejným členy naplánovat provedení a přiřadit obslužná rutina dokončení podřízené aktivity definované v textu člena.  
  
-   `CacheMetadata`: Tento člen poskytne informace potřebné k provedení aktivity modulu runtime. Ve výchozím nastavení, aktivity na `CacheMetadata` metoda bude informovat modul runtime všechny veřejné členy aktivity, ale vzhledem k tomu, že tato aktivita používá soukromé členy pro některé funkce, je nutné informovat runtime jejich existence tak, aby modul runtime můžete mít na paměti je. V takovém případě `CacheMetadata` přepsána funkce tak, aby privátní `valueEnumerator` člen je přístupná. Tento člen také vytváří argument pro hodnoty pro aktivitu, takže je lze předat v aktivitě během provádění.
