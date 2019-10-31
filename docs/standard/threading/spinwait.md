---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
ms.openlocfilehash: 91588fc6e9c3c8e85de6a315c0743efb0137ecd5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128988"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> je odlehčený typ synchronizace, který můžete použít ve scénářích nízké úrovně, abyste se vyhnuli nákladným přepínačům kontextu a přechodům jádra, které jsou potřeba pro události jádra. Pokud se u vícejádrových počítačů neočekává uchovávání prostředků po dlouhou dobu, může být efektivnější pro čekání v uživatelském režimu v několika desítkách nebo několika stovkách cyklů a pak se znovu pokusí získat prostředek. Pokud je prostředek k dispozici po odstřeďování, pak jste uložili několik tisíc cyklů. Pokud prostředek není stále k dispozici, pak jste strávili pouze pár cyklů a stále můžete zadat čekání na bázi jádra. Tato kombinace otáčející se a potom se někdy označuje jako *operace dvoufázové fáze*.  
  
 <xref:System.Threading.SpinWait> je navržena tak, aby se použila ve spojení s typy .NET Framework, které zabalí události jádra, jako je například <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> může použít i samostatně pro základní otáčející se funkce pouze v jednom programu.  
  
 <xref:System.Threading.SpinWait> je více než jen prázdná smyčka. Je pečlivě implementována za účelem zajištění správného chování v případě obecného případu a sám se spustí přepínače kontextu, pokud se dostatečně dlouhou dobu (přibližně doba nutná pro přechod jádra). Například na počítačích s jedním jádrem <xref:System.Threading.SpinWait> přímo vydává časový úsek vlákna, protože rotující bloky přenášejí na všechna vlákna. <xref:System.Threading.SpinWait> také poskytuje i na vícejádrových počítačích, aby se zabránilo čekání v blokování vláken s vyšší prioritou nebo uvolňování paměti. Proto pokud používáte <xref:System.Threading.SpinWait> v dvoufázové operaci čekání, doporučujeme, abyste vyvolali jádro, než <xref:System.Threading.SpinWait> sám zahájí kontextový přepínač. <xref:System.Threading.SpinWait> poskytuje vlastnost <xref:System.Threading.SpinWait.NextSpinWillYield%2A>, kterou lze zaškrtnout před každým voláním <xref:System.Threading.SpinWait.SpinOnce%2A>. Pokud vlastnost vrátí `true`, zahajte svou vlastní operaci čekání. Příklad naleznete v tématu [How to: use objektu SpinWait k implementaci dvoufázové operace wait](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Pokud neprovádíte dvoufázové operace čekání, ale zacházíte do doby splnění nějaké podmínky, můžete povolit, aby <xref:System.Threading.SpinWait> prováděla přepnutí kontextu tak, aby se staly dobrým občanem v prostředí operačního systému Windows. Následující základní příklad ukazuje <xref:System.Threading.SpinWait> v zásobníku bez zámku. Pokud vyžadujete vysoce výkonný zásobník bezpečný pro přístup z více vláken, zvažte použití <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.SpinWait%2A>
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
