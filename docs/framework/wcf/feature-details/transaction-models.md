---
title: Modely transakcí
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: d6c78a5342bf19d19308352cddc241f436bfcb3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745320"
---
# <a name="transaction-models"></a>Modely transakcí
Toto téma popisuje vztah mezi modely programování transakcí a komponentami infrastruktury poskytované společností Microsoft.  
  
 Při použití transakcí v Windows Communication Foundation (WCF) je důležité pochopit, že mezi různými transakčními modely nemusíte vybírat, ale spíše pracujete v různých vrstvách integrovaného a konzistentního modelu.  
  
 V následujících částech jsou popsány tři primární komponenty transakcí.  
  
## <a name="windows-communication-foundation-transactions"></a>Transakce Windows Communication Foundation  
 Podpora transakcí v rámci WCF umožňuje psát transakční služby. Kromě toho s podporou protokolu WS-AtomicTransaction (WS-AT) můžou aplikace přesměrovat transakce na webové služby vytvořené pomocí WCF nebo technologie třetích stran.  
  
 Ve službě nebo aplikaci WCF poskytují funkce transakcí WCF atributy a konfiguraci pro deklarativní určení, jak a kdy má infrastruktura vytvořit, flow a synchronizovat transakce.  
  
## <a name="systemtransactions-transactions"></a>Transakce System. Transactions  
 Obor názvů <xref:System.Transactions> poskytuje explicitní programovací model založený na <xref:System.Transactions.Transaction> třídě a také implicitní programovací model pomocí třídy <xref:System.Transactions.TransactionScope>, ve které infrastruktura automaticky spravuje transakce.  
  
 Další informace o tom, jak vytvořit transakční aplikaci pomocí těchto dvou modelů, najdete v tématu [zápis transakční aplikace](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Ve službě nebo aplikaci WCF poskytuje <xref:System.Transactions> programovací model pro vytváření transakcí v rámci klientské aplikace a pro explicitní interakci s transakcí, pokud je to požadováno, v rámci služby.  
  
## <a name="msdtc-transactions"></a>Transakce MSDTC  
 Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) je správce transakcí, který poskytuje podporu pro distribuované transakce.  
  
 Další informace najdete v referenční příručce [programátora DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).  
  
 Ve službě nebo aplikaci WCF poskytuje služba MSDTC infrastrukturu pro koordinaci transakcí vytvořených v rámci klienta nebo služby.
