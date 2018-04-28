---
title: Modely transakcí
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ab3baf8cc0bb6af951f6f3e6396b7545d0c6b301
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="transaction-models"></a>Modely transakcí
Toto téma popisuje vztah mezi programovací modely transakcí a součásti infrastruktury, které společnost Microsoft poskytuje.  
  
 Při použití transakcí v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], je důležité si uvědomit, že jsou nevyberete mezi různými modely transakcí, ale spíš operační v různých úrovní integrované a konzistentní model.  
  
 Následující části popisují komponenty tři primární transakce.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakce  
 Podpora transakcí v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje zápis transakční služeb. Kromě toho s podporou pro protokol WS-AtomicTransaction (WS-AT), může aplikace tok transakcí webové služby vytvořené pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nebo technologie třetích stran.  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službě nebo aplikaci, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakce funkce poskytují atributy a konfigurace pro deklarativně určení jak a kdy infrastruktury by měl vytvářet, toku a synchronizovat transakce.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions – transakce  
 <xref:System.Transactions> Obor názvů obsahuje oba explicitní programovací model na základě <xref:System.Transactions.Transaction> třídy, jakož i k implicitní programování pomocí modelu <xref:System.Transactions.TransactionScope> třída, ve kterém infrastruktury automaticky spravuje transakce.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Postup vytvoření transakční aplikace pomocí těchto dvou modelů najdete v tématu [zápis transakční aplikace](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službě nebo aplikaci, <xref:System.Transactions> poskytuje programovací model pro vytváření transakcí v rámci klientské aplikace a explicitně interakci s transakci, pokud jsou povinné, v rámci služby.  
  
## <a name="msdtc-transactions"></a>Služba MSDTC transakce  
 Microsoft koordinátora pro distribuované transakce (MSDTC) je správce transakcí, která poskytuje podporu pro distribuované transakce.  
  
 Další informace najdete v tématu [referenční informace pro programátory DTC](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby nebo aplikace, služby MSDTC poskytuje infrastrukturu pro koordinaci transakce vytvořené v rámci klienta nebo služby.
