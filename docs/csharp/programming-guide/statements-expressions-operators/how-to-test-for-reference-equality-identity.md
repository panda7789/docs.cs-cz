---
title: 'Postupy: Testování rovnosti (identity) odkazů (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 78a6bf1f5d4a93bd561faada91b4a11f52692dbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322338"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Postupy: Testování rovnosti (identity) odkazů (Průvodce programováním v C#)
Pro podporu porovnání rovnosti referencí u typů není nutné implementovat žádnou vlastní logiku. Tato funkce je poskytována pro všechny typy statickou metodou <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.  
  
 Následující příklad ukazuje, jak zjistit, jestli mají dvě proměnné *referenční rovnosti*, což znamená, že se vztahují ke stejnému objektu v paměti.  
  
 Příklad také ukazuje, proč <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> vždy vrátí pro typy hodnot hodnotu `false` a proč by nemělo být pro určení rovnosti řetězce použito <xref:System.Object.ReferenceEquals%2A>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 Implementace `Equals` v univerzální základní třídě <xref:System.Object?displayProperty=nameWithType> také provádí kontrolu rovnosti reference, ale nejlepší možností je ji nepoužívat, protože pokud třída přepíše metodu, mohly by být výsledky neočekávané. Totéž platí pro operátory `==` a `!=`. Jsou-li nasazeny na typy referencí, provádí operátory == a `!=` ve výchozím chování kontrolu rovnosti reference. Odvozené třídy však mohou operátor přetížit pro provedení kontroly rovnosti hodnoty. Pokud je třeba zjistit, zda mají dva objekty stejnou rovnost reference, je pro snížení potenciálu výskytu chyby nejlepší použít <xref:System.Object.ReferenceEquals%2A>.  
  
 Konstantní řetězce v rámci stejného sestavení jsou vždy internovány modulem runtime. To znamená, že je zachována pouze jedna instance každého jedinečného textového literálu. Modul runtime však nezaručuje, že jsou řetězce, které jsou vytvořeny v době běhu, internovány, a ani nezaručuje, že jsou internovány dva totožné konstantní řetězce v různých sestaveních.  
  
## <a name="see-also"></a>Viz také  
 [Porovnání rovnosti](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
