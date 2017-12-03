---
title: "Základní programovací životní cyklus"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78ad1159232ecfb75745dd72b7da1e3153a79574
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="basic-programming-lifecycle"></a>Základní programovací životní cyklus
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]umožňuje aplikacím komunikovat, zda jsou na stejném počítači, v Internetu, nebo na jinou aplikaci platformy. Toto téma popisuje úkoly, které jsou nutné k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace. Ukázkovou aplikaci, práce, najdete v části [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Základní úlohy  
 Základní úlohy musíte provést, jsou v pořadí:  
  
1.  Definování kontraktu služby. Kontrakt služby Určuje podpis služby, data, která k výměně a další smluvně požadovaná data. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Implementujte kontrakt. K implementaci kontraktu služby, vytvořte třídu, která implementuje kontrakt a zadejte vlastní chování, které by měly mít modulu runtime. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Konfigurovat službu zadáním koncových bodů a další informace o chování. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Konfigurace služeb](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hostitel služby. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Služby hostování](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Vytvořit klientskou aplikaci. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Vytváření klienti](../../../docs/framework/wcf/building-clients.md).  
  
 I když témata v této části použijte toto pořadí, některé scénáře nespouštějte na začátku. Například pokud chcete k vytvoření klienta pro existující službu, můžete spustit v kroku 5. Nebo pokud vytváříte službu, která budou používat ostatní, může přeskočit krok 5.  
  
 Jakmile jste obeznámeni s vývojem kontraktů služby, můžete si také přečíst [Úvod do rozšíření](../../../docs/framework/wcf/introduction-to-extensibility.md). Pokud máte problémy s vaší služby, zkontrolujte [rychlý start řešení potíží s WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) zobrazíte, zda ostatní uživatelé mají stejné nebo podobné problémy.  
  
## <a name="see-also"></a>Viz také  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
