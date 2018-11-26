---
title: 'Postupy: Testování rovnosti (identity) odkazů (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 4faa674f3f3d65b7c555d7feb9789637f39e9bd7
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296527"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Postupy: Testování rovnosti (identity) odkazů (Průvodce programováním v C#)
Pro podporu porovnání rovnosti referencí u typů není nutné implementovat žádnou vlastní logiku. Tato funkce je poskytována pro všechny typy statickou metodou <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.  
  
 Následující příklad ukazuje, jak zjistit, zda mají dvě proměnné *referenční rovnost*, což znamená, že odkazují na stejný objekt v paměti.  
  
 Příklad také ukazuje, proč <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> vždy vrátí pro typy hodnot hodnotu `false` a proč by nemělo být pro určení rovnosti řetězce použito <xref:System.Object.ReferenceEquals%2A>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 Implementace `Equals` v univerzální základní třídě <xref:System.Object?displayProperty=nameWithType> také provádí kontrolu rovnosti reference, ale nejlepší možností je ji nepoužívat, protože pokud třída přepíše metodu, mohly by být výsledky neočekávané. Totéž platí pro operátory `==` a `!=`. Jsou-li nasazeny v odkazu na typy, výchozí chování `==` a `!=` provádí kontrolu rovnosti reference. Odvozené třídy však mohou operátor přetížit pro provedení kontroly rovnosti hodnoty. Pokud je třeba zjistit, zda mají dva objekty stejnou rovnost reference, je pro snížení potenciálu výskytu chyby nejlepší použít <xref:System.Object.ReferenceEquals%2A>.  
  
 Konstantní řetězce v rámci stejného sestavení jsou vždy internovány modulem runtime. To znamená, že je zachována pouze jedna instance každého jedinečného textového literálu. Modul runtime však nezaručuje, že jsou řetězce, které jsou vytvořeny v době běhu, internovány, a ani nezaručuje, že jsou internovány dva totožné konstantní řetězce v různých sestaveních.  
  
## <a name="see-also"></a>Viz také

- [Porovnání rovnosti](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
