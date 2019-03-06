---
title: Plánování výkonu aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
ms.openlocfilehash: fda5330ff75c1744f3ed9d4394e51b5efb737071
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374424"
---
# <a name="planning-for-application-performance"></a>Plánování výkonu aplikace
Úspěch dosažení svých cílů výkonu závisí na tom, jak dobře při vývoji strategie výkonu. Plánování je první fázi při vývoji libovolný produkt. Toto téma popisuje několik velmi jednoduchých pravidel pro vývoj strategie dobrého výkonu.  
  
## <a name="think-in-terms-of-scenarios"></a>Uvažují v rámci scénáře  
 Scénáře můžete soustředit na důležité komponent vaší aplikace. Scénáře jsou obvykle odvozen z vašich zákazníků, jakož i konkurenčních produktů. Vždy studovat vaše zákazníky a zjistěte, co Opravdu je mezi nimi vlastně těší zpráva o produktu a produktů konkurence. Názory vašich zákazníků můžete určit primární scénáře vaší aplikace. Například pokud navrhujete komponenty, která se použije při spuštění, je pravděpodobné, že součást bude volat pouze jednou při spuštění aplikace. Klíčovým scénářem bude čas spuštění. Další příklady klíčových scénářů může být požadované Snímková frekvence pro animace pořadí nebo maximální pracovní sada pro aplikaci povolená.  
  
## <a name="define-goals"></a>Definování cíle  
 Cíle umožňují určit, zda aplikace pracuje pomaleji, nebo rychleji. Cíle byste měli definovat pro všechny scénáře. Všechna výkonnostní cíle, které definujete by podle očekávání vašich zákazníků. Může být obtížné výkonu sady cílů raném stádiu při vývoji aplikace cyklu, pokud stále existuje řada nevyřešené problémy. Je však lepší nastavit počáteční cíle a zkontrolujte ji později než není mají cíl vůbec.  
  
## <a name="understand-your-platform"></a>Vysvětlení vaši platformu  
 Vždy zachovat cyklu měření, zkoumání, upřesnění a oprava během cyklu vývoje aplikací. Od začátku do konce cyklu vývoje, je nutné měřit výkon vaší aplikace v spolehlivé a stabilní prostředí. Měli byste se vyhnout proměnlivé způsobené externí faktory. Například při testování výkonu, můžete by měl zakázat antivirový program nebo jakékoli automatické aktualizace, jako je SMS, aby ovlivnit výkon výsledky testů. Jakmile se mají měřit výkon vaší aplikace, je potřeba identifikovat změny, které bude mít za následek největší vylepšení. Jakmile vaše aplikace byly upraveny, spuštění cyklu znovu.  
  
## <a name="make-performance-tuning-an-iterative-process"></a>Ujistěte se, iterativní proces pro optimalizaci výkonu  
 Měli byste vědět relativní náklady na jednotlivé funkce, které budete používat. Například použití reflexe v rozhraní Microsoft .NET Framework je obvykle výkon náročné z hlediska výpočetních prostředků, takže byste měli používat uvážlivě. Neznamená to, aby využívání reflection, pouze, měli byste být opatrní k vyrovnávání požadavků na výkon vaší aplikace pomocí funkcí, které používáte požadavky na výkon.  
  
## <a name="build-towards-graphical-richness"></a>Sestavení pro grafické kombinujícím  
 Představuje klíčovou techniku pro vytváření škálovatelných přístup k dosažení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] výkon aplikace, je vytvořit pro grafické kombinujícím funkce a složitost. Vždy začněte s použitím nejméně náročné na prostředky výkonu k dosažení cílů scénář. Po dosažení těchto cílů sestavení směrem k grafické kombinujícím pomocí více funkcí náročné na výkon, vždy dodržujte při tom cílů scénář. Mějte na paměti, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je velmi velké množství platformy a poskytuje velmi velké množství grafické funkce. Pomocí funkce náročné na výkon bez přemýšlení může mít negativní vliv na výpočetní výkon.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky jsou ze své podstaty extensible tím, že pro přizpůsobení šíření celého jejich výskytu, při není změna jejich chování ovládacího prvku. S využitím styly, šablony a šablony ovládacích prvků, můžete vytvořit a postupně vyvíjí přizpůsobitelnou [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , která se přizpůsobí vašim požadavkům na výkon.  
  
## <a name="see-also"></a>Viz také:
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
