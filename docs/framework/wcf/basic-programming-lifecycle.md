---
title: Základní programovací životní cyklus
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: d5322dfca1aa006ba2fc85b5dedebd09941f9c0e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499220"
---
# <a name="basic-programming-lifecycle"></a>Základní programovací životní cyklus
Windows Communication Foundation (WCF) umožňuje aplikacím komunikovat, jestli jsou na stejném počítači, na Internetu, nebo na různých aplikačních platformách. Toto téma popisuje úlohy, které jsou nutné k vytvoření aplikace WCF. Ukázkové aplikace práci, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Základní úlohy  
 Provádět základní úlohy jsou v pořadí:  
  
1.  Definování kontraktu služby. Kontrakt služby specifikuje podpis služby, data, která jej vymění a dalších smluvně požadovaná data. Další informace najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Implementujte kontrakt. Implementace kontraktu služby, vytvořte třídu, která implementuje tento kontrakt a zadejte vlastní chování, které by měly mít modulu runtime. Další informace najdete v tématu [implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Nakonfigurujte službu tak, že zadáte koncové body a další informace o chování. Další informace najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hostování služby. Další informace najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Sestavení klientské aplikace. Další informace najdete v tématu [sestavování klientů](../../../docs/framework/wcf/building-clients.md).  
  
 I když témata v této části použijte toto pořadí, některé scénáře, nespouštějte na začátku. Například pokud chcete vytvořit klienta pro už existující službu, můžete začít v kroku 5. Nebo pokud vytváříte službu, která bude používat ostatní, můžete přeskočit krok 5.  
  
 Jakmile máte zkušenosti s vývojem kontrakty služeb, můžete si také přečíst [Úvod do rozšíření](../../../docs/framework/wcf/introduction-to-extensibility.md). Pokud máte problémy s vaší službou, zkontrolujte [rychlý start řešení potíží s WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) abyste zjistili, jestli ostatní jsou stejné nebo podobné problémy.  
  
## <a name="see-also"></a>Viz také:
- [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
