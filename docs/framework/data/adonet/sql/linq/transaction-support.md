---
title: Podpora transakcí
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792272"
---
# <a name="transaction-support"></a>Podpora transakcí
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje tři různé transakční modely. V následujícím seznamu jsou uvedeny modely v pořadí provedených kontrol.  
  
## <a name="explicit-local-transaction"></a>Explicitní místní transakce  
 Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána <xref:System.Data.Linq.DataContext.Transaction%2A> vlastnost, pokud je vlastnost nastavena na transakci <xref:System.Data.Linq.DataContext.SubmitChanges%2A> (`IDbTransaction`), volání je provedeno v kontextu stejné transakce.  
  
 Po úspěšném provedení transakce máte zodpovědnost za potvrzení nebo vrácení transakce zpět. Připojení odpovídající transakci se musí shodovat s připojením použitým pro sestavování <xref:System.Data.Linq.DataContext>. Pokud se používá jiné připojení, je vyvolána výjimka.  
  
## <a name="explicit-distributable-transaction"></a>Explicitní Distribuovatelný transakce  
 Můžete volat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API (mimo <xref:System.Data.Linq.DataContext.SubmitChanges%2A>jiné) v oboru aktivního <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zjistí, že se volání nachází v oboru transakce a nevytváří novou transakci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]v tomto případě se také vyhnete ukončení připojení. Dotaz a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> spuštění můžete provádět v kontextu takové transakce.  
  
## <a name="implicit-transaction"></a>Implicitní transakce  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Když zavoláte [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , zkontroluje, jestli je volání <xref:System.Transactions.Transaction> v oboru, nebo pokud `Transaction` je vlastnost (`IDbTransaction`) nastavená na místní transakci zahájenou uživatelem. Pokud nenajde žádnou transakci, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí místní transakci (`IDbTransaction`) a použije ji k provedení generovaných příkazů SQL. Po úspěšném dokončení všech příkazů SQL se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] potvrdí místní transakce a vrátí.  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
- [Postupy: Odesílání dat v závorkách pomocí transakcí](how-to-bracket-data-submissions-by-using-transactions.md)
