---
title: Vytváření vlastních aktivit řízení toku
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: f457e6f8cefd7183ca20cb449adf1ac15d7bde79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647147"
---
# <a name="creating-custom-flow-control-activities"></a>Vytváření vlastních aktivit řízení toku
Rozhraní .NET Framework obsahuje širokou škálu aktivit řízení toku, které fungují podobně jako abstraktní programovací struktury (například <xref:System.Activities.Statements.Flowchart>) nebo standardní programovacích příkazů (například <xref:System.Activities.Statements.If>). Toto téma se věnuje architektuře jednoho z ukázkových projektů [neobecné ForEach](./samples/non-generic-foreach.md).  
  
## <a name="creating-the-custom-class"></a>Vytvoření vlastní třídy  
 Protože třída neobecné ForEach muset naplánovat podřízené aktivity, ji budou muset být odvozen od <xref:System.Activities.NativeActivity>, od aktivit, které jsou odvozeny z <xref:System.Workflow.Activities.CodeActivity> tuto funkci nemají.  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 Vlastní třída vyžaduje několik členů pro uložení data používaná aktivitou a poskytuje funkce pro spuštění aktivity podřízené aktivity. Tyto členy, patří:  
  
- `valueEnumerator`: Neveřejné <xref:System.Activities.Variable%601> typu <xref:System.Collections.IEnumerator> použité k iteraci přes kolekci položek. Tento člen je typu <xref:System.Activities.Variable%601> vzhledem k tomu, že se používá interně v činnosti, spíše než argument nebo veřejná vlastnost, která se použije, pokud mají původ mimo aktivitu tento objekt.  
  
- `OnChildComplete`: Veřejná <xref:System.Activities.CompletionCallback> vlastnost, která se spustí po dokončení provádění jednotlivých podřízených. Tento člen je definován jako vlastnosti CLR, protože jeho hodnota se nezmění pro různé instance aktivity.  
  
- `Values`: Kolekce vstupů pro iterace podřízené aktivity. Tento člen je typu <xref:System.Activities.InArgument%601>, protože je zdrojem dat mimo aktivitu, ale obsah kolekce se neočekává změna během provádění aktivity. V případě potřeby funkci chcete-li změnit obsah této kolekce při provádění aktivity (k přidávání nebo odebírání aktivit, například) aktivity tento člen by byl definovaný jako <xref:System.Activities.ActivityAction>, které by byly vyhodnocovány pokaždé, když To se použila, takže změny budou k dispozici pro aktivity.  
  
- `Body`: Tento člen definuje aktivitu spustit pro každou položku v `Values` kolekce. Tento člen je definován jako <xref:System.Activities.ActivityAction> tak, aby je vyhodnocen vždy, když je přístupný.  
  
- `Execute`: Tato metoda používá `InternalExecute`, `OnForEachComplete`, a `GetStateAndExecute` neveřejné členy naplánovat spuštění a přiřaďte obslužné rutiny dokončení podřízené aktivity definované v těle členu.  
  
- `CacheMetadata`: Tento člen modul runtime poskytuje informace potřebné ke spuštění aktivity. Ve výchozím nastavení, aktivity vaší `CacheMetadata` metoda informuje runtime všechny veřejné členy aktivity, ale vzhledem k tomu, že tato aktivita používá soukromé členy pro některé funkce, je potřeba informovat runtime jejich existenci tak, aby modul runtime může mít na paměti je. V takovém případě `CacheMetadata` přepsat funkci tak, aby privátní `valueEnumerator` člen je přístupný. Tento člen také vytvoří argument hodnoty pro aktivitu tak, aby se může být předán v aktivity za běhu.
