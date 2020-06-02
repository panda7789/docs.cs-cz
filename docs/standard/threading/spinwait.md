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
ms.openlocfilehash: 8b98e7d8b8ea4578fb446a0587f9a46ba4271348
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291107"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>je odlehčený typ synchronizace, který můžete použít ve scénářích nízké úrovně, abyste se vyhnuli nákladným přepínačům kontextu a přechodům jádra vyžadovaným pro události jádra. Pokud se u vícejádrových počítačů neočekává uchovávání prostředků po dlouhou dobu, může být efektivnější pro čekání v uživatelském režimu v několika desítkách nebo několika stovkách cyklů a pak se znovu pokusí získat prostředek. Pokud je prostředek k dispozici po odstřeďování, pak jste uložili několik tisíc cyklů. Pokud prostředek není stále k dispozici, pak jste strávili pouze pár cyklů a stále můžete zadat čekání na bázi jádra. Tato kombinace otáčející se a potom se někdy označuje jako *operace dvoufázové fáze*.  
  
 <xref:System.Threading.SpinWait>je určena k použití ve spojení s .NET Framework typy, které zabalí události jádra, například <xref:System.Threading.ManualResetEvent> . <xref:System.Threading.SpinWait>dá se použít i samostatně pro základní otáčející se funkce pouze v jednom programu.  
  
 <xref:System.Threading.SpinWait>je více než jenom prázdná smyčka. Je pečlivě implementována za účelem zajištění správného chování v případě obecného případu a sám se spustí přepínače kontextu, pokud se dostatečně dlouhou dobu (přibližně doba nutná pro přechod jádra). Například na počítačích s jedním jádrem <xref:System.Threading.SpinWait> poskytuje časové období vlákna okamžitě, protože rotující bloky přenášejí na všechna vlákna. <xref:System.Threading.SpinWait>také poskytuje i na vícejádrových počítačích, aby se zabránilo čekání v blokování vláken s vyšší prioritou nebo uvolňování paměti. Proto pokud používáte <xref:System.Threading.SpinWait> v dvoufázové operaci čekání, doporučujeme, abyste vyvolali jádro před tím, než <xref:System.Threading.SpinWait> sám zahájí kontextový přepínač. <xref:System.Threading.SpinWait>poskytuje <xref:System.Threading.SpinWait.NextSpinWillYield%2A> vlastnost, kterou lze zaškrtnout před každým voláním metody <xref:System.Threading.SpinWait.SpinOnce%2A> . Jakmile se vlastnost vrátí `true` , inicializujte svou vlastní operaci čekání. Příklad naleznete v tématu [How to: use objektu SpinWait k implementaci dvoufázové operace wait](how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Pokud neprovádíte dvoufázové operace čekání, ale zacházíte do doby, kdy je podmínka pravdivá, můžete povolit <xref:System.Threading.SpinWait> provádění kontextových přepínačů, aby se jedná o dobrého občana v prostředí operačního systému Windows. Následující základní příklad ukazuje <xref:System.Threading.SpinWait> v zásobníku bez zámku. Pokud vyžadujete vysoce výkonný zásobník bezpečný pro přístup z více vláken, zvažte použití <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> .  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread.SpinWait%2A>
- [Dělení objektů a funkcí](threading-objects-and-features.md)
