---
title: 'Postupy: Test rovnosti (Identity) - odkazů C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 057532cae42d7a0b6d11750ae0e33e43108cfda9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678904"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a>Postupy: Test rovnosti (Identity) odkazů (C# Průvodce programováním v)
Pro podporu porovnání rovnosti referencí u typů není nutné implementovat žádnou vlastní logiku. Tato funkce je poskytována pro všechny typy statickou metodou <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>.  
  
 Následující příklad ukazuje, jak zjistit, zda mají dvě proměnné *referenční rovnost*, což znamená, že odkazují na stejný objekt v paměti.  
  
 Příklad také ukazuje, proč <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> vždy vrátí pro typy hodnot hodnotu `false` a proč by nemělo být pro určení rovnosti řetězce použito <xref:System.Object.ReferenceEquals%2A>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideObjects#90](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#90)]  
  
 Implementace `Equals` v univerzální základní třídě <xref:System.Object?displayProperty=nameWithType> také provádí kontrolu rovnosti reference, ale nejlepší možností je ji nepoužívat, protože pokud třída přepíše metodu, mohly by být výsledky neočekávané. Totéž platí pro operátory `==` a `!=`. Jsou-li nasazeny v odkazu na typy, výchozí chování `==` a `!=` provádí kontrolu rovnosti reference. Odvozené třídy však mohou operátor přetížit pro provedení kontroly rovnosti hodnoty. Pokud je třeba zjistit, zda mají dva objekty stejnou rovnost reference, je pro snížení potenciálu výskytu chyby nejlepší použít <xref:System.Object.ReferenceEquals%2A>.  
  
 Konstantní řetězce v rámci stejného sestavení jsou vždy internovány modulem runtime. To znamená, že je zachována pouze jedna instance každého jedinečného textového literálu. Modul runtime však nezaručuje, že jsou řetězce, které jsou vytvořeny v době běhu, internovány, a ani nezaručuje, že jsou internovány dva totožné konstantní řetězce v různých sestaveních.  
  
## <a name="see-also"></a>Viz také:

- [Porovnání rovnosti](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
