---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961138"
---
# <a name="operating-system-resources-required-by-wcf"></a>Prostředky operačního systému požadované službou WCF

Windows Communication Foundation (WCF) závisí na několika prostředcích, které poskytuje operační systém k fungování. Následující tabulka uvádí tyto prostředky:

|Partner|Popis|
|--------------|-----------------|
|Microsoft DTC (Distributed Transaction Coordinator) (MSDTC)|Vyžaduje se pro podporu transakcí OleTx.|
|Internet Information Services (IIS)|Povinné, pokud chcete použít službu IIS k hostování aplikace.|
|Aktivační služba procesů systému Windows (WAS)|Vyžadováno, pokud chcete použít k hostování aplikace.|
