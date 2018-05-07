---
title: Nedostatek místa v zásobníku (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="out-of-stack-space-visual-basic"></a>Nedostatek místa v zásobníku (Visual Basic)
Zásobník představuje pracovní oblasti paměti, která zvětšují a zvětšování dynamicky s požadavky vaší provádění programu. Jeho omezení byly překročeny.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, že nejsou postupy vnořeny příliš hluboko.  
  
2.  Zajistěte, aby rekurzivní procedury ukončit správně.  
  
3.  Pokud místní proměnné vyžadovat další místní proměnné místa na disku než je k dispozici, zkuste deklarace některé proměnné na úrovni modulu. Můžete také deklarovat všechny proměnné v postupu statické tak, že před `Property`, `Sub`, nebo `Function` – klíčové slovo s `Static`. Nebo můžete použít `Static` příkaz deklarovat jednotlivých statické proměnné v rámci procedury.  
  
4.  Některé z vaší řetězce pevné délky jako proměnné délky řetězce, znovu definujte jako řetězce pevné délky použijte více místa v zásobníku než proměnné délky řetězce. Můžete také definovat řetězec na úrovni modulu vyžaduje na žádné místa v zásobníku.  
  
5.  Zkontrolujte počet vnořených `DoEvents` funkce volání, pomocí `Calls` dialogové okno pro zobrazení, které postupy jsou aktivní v zásobníku.  
  
6.  Zkontrolujte, zda že jste nezpůsobila "cascade událostí" podle aktivuje událost, která volá proceduru události, které jsou již v zásobníku. Událost v kaskádě je podobná neukončený rekurzivní volání procedur, ale je méně zřejmé, protože při volání jazyka Visual Basic spíše než explicitní volání v kódu. Použití `Calls` dialogové okno pro zobrazení, které postupy jsou aktivní v zásobníku.  
  
## <a name="see-also"></a>Viz také  
 [Okna paměti](/visualstudio/debugger/memory-windows)
