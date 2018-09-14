---
title: Zámky modulů pro čtení a zápis
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8be9b4eef30333fbbdc26915635d17157176d6fc
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513492"
---
# <a name="reader-writer-locks"></a>Zámky modulů pro čtení a zápis
<xref:System.Threading.ReaderWriterLockSlim> Třída umožňuje více vláken souběžně číst prostředek, ale vyžaduje vlákno čekat výhradní zámek, chcete-li k prostředku.  
  
 Můžete použít <xref:System.Threading.ReaderWriterLockSlim> ve vaší aplikaci zajistit kooperativní synchronizace mezi vlákny, které přistupují k sdíleného prostředku. Uzamčení se přesunete <xref:System.Threading.ReaderWriterLockSlim> samotný.  
  
 Jak se každý použitý mechanizmus synchronizace vlákna, musíte zajistit, že žádná vlákna obejít blokování, která je poskytována <xref:System.Threading.ReaderWriterLockSlim>. Jeden způsob, jak to zajistit je návrh třídu, která zapouzdřuje sdíleného prostředku. Tato třída by poskytovaly členy, které využívají privátní sdíleného prostředku a používají privátní <xref:System.Threading.ReaderWriterLockSlim> pro synchronizaci. Příklad, podívejte se na příklad kódu pro <xref:System.Threading.ReaderWriterLockSlim> třídy. <xref:System.Threading.ReaderWriterLockSlim> je dostatečně účinný, který se má použít k synchronizaci jednotlivých objektů.  
  
 Struktury vaší aplikaci minimalizovat dobu trvání pro čtení a operace zápisu. Operace zápisu dlouhé ovlivnit propustnost přímo, protože je výhradní zámek pro zápis. Dlouho přečíst operace blokovat čekání zapisovače a pokud alespoň jedno vlákno čeká přístup pro zápis, vlákna, které vyžadují přístup pro čtení se zablokuje, stejně.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Má dvě zámky pro čtení a zápis, <xref:System.Threading.ReaderWriterLockSlim> a <xref:System.Threading.ReaderWriterLock>. <xref:System.Threading.ReaderWriterLockSlim> doporučuje se pro všechny vývoj nových projektů. <xref:System.Threading.ReaderWriterLockSlim> je podobný <xref:System.Threading.ReaderWriterLock>, ale zjednodušila pravidla pro rekurzi a pro upgrade a Downgrade Stav zámku. <xref:System.Threading.ReaderWriterLockSlim> předchází mnoha případech potenciální zablokování. Kromě toho výkon <xref:System.Threading.ReaderWriterLockSlim> je výrazně lepší než <xref:System.Threading.ReaderWriterLock>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ReaderWriterLockSlim>  
- <xref:System.Threading.ReaderWriterLock>  
- [Dělení na vlákna](../../../docs/standard/threading/index.md)  
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
