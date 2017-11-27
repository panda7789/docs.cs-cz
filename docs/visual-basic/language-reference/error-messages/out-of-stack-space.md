---
title: "Nedostatek místa v zásobníku (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a>Nedostatek místa v zásobníku (Visual Basic)
Zásobník představuje pracovní oblasti paměti, která zvětšují a zvětšování dynamicky s požadavky vaší provádění programu. Jeho omezení byly překročeny.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, že nejsou postupy vnořeny příliš hluboko.  
  
2.  Zajistěte, aby rekurzivní procedury ukončit správně.  
  
3.  Pokud místní proměnné vyžadovat další místní proměnné místa na disku než je k dispozici, zkuste deklarace některé proměnné na úrovni modulu. Můžete také deklarovat všechny proměnné v postupu statické tak, že před `Property`, `Sub`, nebo `Function` – klíčové slovo s `Static`. Nebo můžete použít `Static` příkaz deklarovat jednotlivých statické proměnné v rámci procedury.  
  
4.  Některé z vaší řetězce pevné délky jako proměnné délky řetězce, znovu definujte jako řetězce pevné délky použijte více místa v zásobníku než proměnné délky řetězce. Můžete také definovat řetězec na úrovni modulu vyžaduje na žádné místa v zásobníku.  
  
5.  Zkontrolujte počet vnořených `DoEvents` funkce volání, pomocí `Calls` dialogové okno pro zobrazení, které postupy jsou aktivní v zásobníku.  
  
6.  Zkontrolujte, zda že jste nezpůsobila "cascade událostí" podle aktivuje událost, která volá proceduru události, které jsou již v zásobníku. Událost v kaskádě je podobná neukončený rekurzivní volání procedur, ale je méně zřejmé, vzhledem k tomu, že se provedené volání [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] místo explicitní volání v kódu. Použití `Calls` dialogové okno pro zobrazení, které postupy jsou aktivní v zásobníku.  
  
## <a name="see-also"></a>Viz také  
 [Okna paměti](/visualstudio/debugger/memory-windows)
