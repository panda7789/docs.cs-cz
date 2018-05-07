---
title: Základní programovací životní cyklus
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: df86b0750a0fb8760d77fa36ec0806a1c5a9c0a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basic-programming-lifecycle"></a>Základní programovací životní cyklus
Windows Communication Foundation (WCF) umožňuje aplikacím komunikovat, zda jsou na stejném počítači, v Internetu, nebo na jinou aplikaci platformy. Toto téma popisuje úkoly, které jsou nutné k vytvoření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace. Ukázkovou aplikaci, práce, najdete v části [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Základní úlohy  
 Základní úlohy musíte provést, jsou v pořadí:  
  
1.  Definování kontraktu služby. Kontrakt služby Určuje podpis služby, data, která k výměně a další smluvně požadovaná data. Další informace najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Implementujte kontrakt. K implementaci kontraktu služby, vytvořte třídu, která implementuje kontrakt a zadejte vlastní chování, které by měly mít modulu runtime. Další informace najdete v tématu [implementace kontraktů služby](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Konfigurovat službu zadáním koncových bodů a další informace o chování. Další informace najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hostitel služby. Další informace najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Vytvořit klientskou aplikaci. Další informace najdete v tématu [sestavování klientů](../../../docs/framework/wcf/building-clients.md).  
  
 I když témata v této části použijte toto pořadí, některé scénáře nespouštějte na začátku. Například pokud chcete k vytvoření klienta pro existující službu, můžete spustit v kroku 5. Nebo pokud vytváříte službu, která budou používat ostatní, může přeskočit krok 5.  
  
 Jakmile jste obeznámeni s vývojem kontraktů služby, můžete si také přečíst [Úvod do rozšíření](../../../docs/framework/wcf/introduction-to-extensibility.md). Pokud máte problémy s vaší služby, zkontrolujte [rychlý start řešení potíží s WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) zobrazíte, zda ostatní uživatelé mají stejné nebo podobné problémy.  
  
## <a name="see-also"></a>Viz také  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
