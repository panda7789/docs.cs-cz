---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: ac9bd5ed7c2092720c6521d0f78185c3fbf9f94b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318945"
---
# <a name="operating-system-resources-required-by-wcf"></a>Prostředky operačního systému požadované službou WCF
Windows Communication Foundation (WCF) závisí na několika prostředcích, které poskytuje operační systém k fungování. Následující tabulka uvádí tyto prostředky.  
  
|Partner|Popis|  
|--------------|-----------------|  
|Microsoft DTC (Distributed Transaction Coordinator) (MSDTC)|Vyžaduje se pro podporu transakcí OleTx.|  
|Internet Information Services (IIS)|Povinné, pokud chcete použít službu IIS k hostování aplikace.|  
|Aktivační služba procesů systému Windows (WAS)|Vyžadováno, pokud chcete použít k hostování aplikace.|  
  
## <a name="see-also"></a>Viz také:

- [Požadavky na systém](wcf-system-requirements.md)
