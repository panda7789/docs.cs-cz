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
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="3b81c-102">Prostředky operačního systému požadované službou WCF</span><span class="sxs-lookup"><span data-stu-id="3b81c-102">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="3b81c-103">Windows Communication Foundation (WCF) závisí na několika prostředcích, které poskytuje operační systém k fungování.</span><span class="sxs-lookup"><span data-stu-id="3b81c-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="3b81c-104">Následující tabulka uvádí tyto prostředky:</span><span class="sxs-lookup"><span data-stu-id="3b81c-104">The following table lists those resources:</span></span>

|<span data-ttu-id="3b81c-105">Partner</span><span class="sxs-lookup"><span data-stu-id="3b81c-105">Resource</span></span>|<span data-ttu-id="3b81c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3b81c-106">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="3b81c-107">Microsoft DTC (Distributed Transaction Coordinator) (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="3b81c-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="3b81c-108">Vyžaduje se pro podporu transakcí OleTx.</span><span class="sxs-lookup"><span data-stu-id="3b81c-108">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="3b81c-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="3b81c-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="3b81c-110">Povinné, pokud chcete použít službu IIS k hostování aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b81c-110">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="3b81c-111">Aktivační služba procesů systému Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="3b81c-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="3b81c-112">Vyžadováno, pokud chcete použít k hostování aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b81c-112">Required if you want to use WAS to host your application.</span></span>|
