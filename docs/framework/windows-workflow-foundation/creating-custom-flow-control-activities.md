---
title: Vytváření vlastních aktivit řízení toku
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 8e7d4caad197631509fe80a5b5a08eff4d228c1c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989720"
---
# <a name="creating-custom-flow-control-activities"></a>Vytváření vlastních aktivit řízení toku
.NET Framework obsahuje různé aktivity řízení toku, které fungují podobně jako abstraktní programové struktury (například <xref:System.Activities.Statements.Flowchart>) nebo standardní programovací příkazy ( <xref:System.Activities.Statements.If>například). Toto téma popisuje architekturu jednoho z ukázkových projektů, [které nepatří do obecného příkazu foreach](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Vytvoření vlastní třídy  
 Vzhledem k tomu, že neobecná třída foreach bude potřebovat naplánovat podřízené aktivity, bude nutné odvozovat z <xref:System.Activities.NativeActivity>, protože aktivity odvozené z <xref:System.Workflow.Activities.CodeActivity> nemají tuto funkci.  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 Vlastní třída vyžaduje několik členů, aby ukládala data používaná aktivitou a poskytovala funkcionalitu pro provádění podřízených aktivit aktivity. Mezi tyto členy patří:  
  
- `valueEnumerator`: <xref:System.Activities.Variable%601> Typ<xref:System.Collections.IEnumerator> , který se používá k iteraci v kolekci položek, není veřejný. Tento člen je typu <xref:System.Activities.Variable%601> , protože se používá interně v aktivitě, nikoli argument nebo veřejnou vlastnost, která by se použila v případě, že by tento objekt měl mít původ mimo aktivitu.  
  
- `OnChildComplete`: Veřejná <xref:System.Activities.CompletionCallback> vlastnost, která se spustí, když každý podřízený uzel dokončí provádění. Tento člen je definován jako vlastnost CLR, protože jeho hodnota se nemění pro různé instance aktivity.  
  
- `Values`: Kolekce vstupů použitých pro iterace podřízené aktivity. Tento člen je typu <xref:System.Activities.InArgument%601>, protože počátek dat je mimo aktivitu, ale během provádění aktivity se neočekává, že se v obsahu kolekce mění. Pokud aktivita potřebuje funkci ke změně obsahu této kolekce v době, kdy byla aktivita spuštěná (pro přidání nebo odebrání aktivit), bude tento člen definovaný jako <xref:System.Activities.ActivityAction>, který by se pak vyhodnotil pokaždé, když bylo k němu přístup, aby byla pro aktivitu k dispozici změny.  
  
- `Body`: Tento člen definuje aktivitu, která má být provedena pro každou položku v `Values` kolekci. Tento člen je definován jako <xref:System.Activities.ActivityAction> , aby byl vyhodnocen při každém jeho použití.  
  
- `Execute`: Tato metoda používá `InternalExecute` `OnForEachComplete`neveřejné členy k naplánování spuštění a přiřazení obslužné rutiny dokončení podřízené aktivity definované v těle člena. `GetStateAndExecute`  
  
- `CacheMetadata`: Tento člen poskytuje modul runtime s informacemi, které potřebuje k provedení aktivity. Ve výchozím nastavení bude `CacheMetadata` metoda aktivity informovat modul runtime všech veřejných členů aktivity, ale vzhledem k tomu, že tato aktivita používá pro některé funkce soukromé členy, musí informovat modul runtime své existence, aby mohl modul runtime vědět ihned. V tomto případě `CacheMetadata` je funkce přepsána tak, aby byl `valueEnumerator` k soukromému členu umožněn pøístup. Tento člen také vytvoří argument pro hodnoty aktivity tak, aby je bylo možné předat do aktivity během provádění.
