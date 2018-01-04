---
title: "Plánování výkonu aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6bdb140d90de02fa817c55a05f40e57fcd0d636c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="planning-for-application-performance"></a>Plánování výkonu aplikace
Úspěch dosažení výkonnostní cíle, závisí na tom, jak dobře vývoj strategie výkonu. Plánování je první fázi ve vývoji některý z produktů. Toto téma popisuje několik velmi jednoduchých pravidel pro vývoj strategie dobrý výkon.  
  
## <a name="think-in-terms-of-scenarios"></a>Vezměte v úvahu z hlediska scénáře  
 Scénáře můžete soustředit na důležité součásti vaší aplikace. Scénáře jsou obecně odvozená od vašeho zákazníků, jakož i konkurenční produkty. Vždy prostudovali vaši zákazníci a zjistit, co opravdu umožňuje jejich nadšení o produktu a vašich konkurentů produkty. Názory zákazníků můžete určit primární scénář vaší aplikace. Například pokud navrhujete komponenty, která se použije při spuštění, je pravděpodobné, že bude lze komponentu volat pouze jednou, při spuštění aplikace. Čas spuštění se změní na váš scénář klíče. Další příklady klíčových scénářů může být požadované snímků za sekundu pro animace pořadí, nebo maximální pracovní sadu pro aplikaci povolena.  
  
## <a name="define-goals"></a>Definování cílů  
 Cíle umožňují určit, zda aplikace pracuje pomaleji nebo rychlejší. Měli byste cíle pro všechny vaše scénáře. Všechna výkonnostní cíle, které definujete by měla být založena na očekávání vašich zákazníků. Může být obtížné výkonu sadu cílů již v rané fázi na při vývoji aplikace cyklus, když jsou stále mnoho nevyřešené problémy. Je nicméně lepší nastavit počáteční cílem a zkontrolujte ji později než k nemá cílem vůbec.  
  
## <a name="understand-your-platform"></a>Pochopení vaši platformu  
 Vždy udržujte cyklus měření příčin, upřesnění nebo odstranění cyklu vývoje aplikace. Od začátku do konce cyklu vývoje, budete muset měřit výkon aplikace v prostředí spolehlivou a stabilní. Neměli byste variabilita způsobené externí faktory. Například při testování výkonu, můžete měli zakázat antivirový či jakékoli automatických aktualizací, například SMS, aby nebyla dopad výkonu výsledky testu. Jakmile se mají měřit výkon aplikace, musíte určit změny, které bude mít za následek největších vylepšení. Jakmile změníte vaší aplikace, spusťte znovu cyklu.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Ujistěte se, iterativní proces optimalizace výkonu  
 Měli byste vědět relativní náklady na jednotlivé funkce, které chcete použít. Například použití reflexe v [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] je obecně výkon náročné z hlediska výpočetních prostředků, proto je vhodné použít uvážlivě. To neznamená vyhnout se použití reflexe, pouze zda je třeba pečlivě vyvážit požadavky na výkon vaší aplikace s požadavky výkonu funkce, které používáte.  
  
## <a name="build-towards-graphical-richness"></a>Sestavení směrem grafické Zvučnost  
 Klíče technika pro vytváření škálovatelných přístup k dosahování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkon aplikace je k sestavení směrem grafické zvučnost a složitost. Vždy spusťte s použitím minimálně výkonu náročné prostředky k dosažení cílů scénář. Po dosažení těchto cílů sestavení směrem grafické zvučnost pomocí další funkce náročné výkonu, nezapomeňte udržování cílů scénář. Pamatujte si, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je velmi platformu a poskytuje velmi bohaté grafické funkce. Pomocí funkce náročné výkonu bez přemýšlení může negativně ovlivnit výkon celkové aplikace.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ovládací prvky jsou ze své podstaty extensible tím, že pro hromadné přizpůsobení vzhledu při není změna jejich chování ovládacího prvku. Využitím styly, šablony dat a řízení šablony, můžete vytvořit a přírůstkově momentální nastavit vlastní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] který přizpůsobí vašim požadavkům na výkon.  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další výkonnostní doporučení](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
