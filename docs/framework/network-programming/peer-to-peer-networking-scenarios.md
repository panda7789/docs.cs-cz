---
title: Scénáře pro sítě peer-to-peer
ms.date: 03/30/2017
ms.assetid: d23b1a64-2e08-4014-882a-c1dd766bdcc2
ms.openlocfilehash: 9b5d4d35085585fe04f2f0c0a105e6dff4b1fcc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623084"
---
# <a name="peer-to-peer-networking-scenarios"></a>Scénáře pro sítě peer-to-peer

Síť typu peer-to-peer umožňuje nebo vylepšuje následující scénáře:

## <a name="real-time-communications-rtc"></a>Komunikace v reálném čase (RTC)

- Zasílání rychlých zpráv bez serveru

  RTC existuje dnes. Uživatelé počítačů mohou chatovat a mít hlasové nebo video konverzace se svými vrstevníky dnes. Mnoho existujících programů a jejich komunikačních protokolů však závisí na tom, že servery budou fungovat. Pokud se účastníte bezdrátové sítě ad hoc nebo jste součástí izolované sítě, nemůžete tato zařízení RTC používat. Technologie peer-to-peer umožňuje rozšíření rtc technologií do těchto dalších síťových prostředí.

- Dohazování v reálném čase a hratelnost

  Podobně jako RTC, real-time hra existuje dnes. Existuje mnoho webových herních stránek, které obstarávají herní komunitu přes internet. Nabízejí možnost najít jiné hráče s podobnými zájmy a hrát hru společně. Problém je v tom, že herní stránky existují pouze na internetu a jsou zaměřeny na vášnivý hráč, který chce hrát proti nejlepším hráčům na světě. Tyto stránky sledovat a poskytovat statistiky, které pomáhají v procesu. Tyto weby však neumožňují hráči nastavit ad-hoc hru mezi přáteli v různých síťových prostředích. Tuto funkci může poskytovat síť peer-to-peer.

## <a name="collaboration"></a>Spolupráce

- Řešení pracovních prostorů pro projekt

  Sdílené aplikace pracovního prostoru umožňují vytváření ad hoc pracovních skupin a pak umožňují vlastníkům pracovních skupin naplnit sdílený pracovní prostor nástroji a obsahem, které skupině umožní vyřešit problém. To může zahrnovat vývěsky, nástroje pro zvýšení produktivity a soubory.

- Sdílení souborů s ostatními

  Podmnožinou sdílení pracovního prostoru projektu je možnost sdílet soubory. Přestože tato schopnost existuje dnes s aktuální verzí systému Windows, může být rozšířena prostřednictvím sítě peer-to-peer, aby byl obsah souborů k dispozici snadným a přátelským způsobem. Umožňuje snadný přístup k neuvěřitelné mušle obsahu na okraji internetu nebo v ad-hoc výpočetníprostředí zvyšuje hodnotu síťové výpočetní techniky.

- Sdílení zkušeností

  S bezdrátovým připojením stále více převládající, peer-to-peer sítí vám umožní být on-line ve skupině vrstevníků a být schopen sdílet své zkušenosti (jako je západ slunce, rockový koncert, nebo dovolenou cruise), zatímco oni se vyskytují.

## <a name="content-distribution"></a>Distribuce obsahu

- Textové zprávy

  Síť peer-to-peer může umožnit šíření textových informací ve formě souborů nebo zpráv velké skupině uživatelů. Příkladem je seznam novinek.

- Zvuk a video

  Síť peer-to-peer může také umožnit šíření zvukových nebo video informací velké skupině uživatelů, jako je například velký koncert nebo firemní setkání. Chcete-li distribuovat obsah dnes, je nutné nakonfigurovat vysokokapacitní servery shromažďovat a distribuovat zatížení stovky nebo tisíce uživatelů. Díky sítím typu peer-to-peer by pouze hrstka partnerů skutečně získala svůj obsah z centralizovaných serverů. Tito vrstevníci by zaplavili tyto informace několika dalším lidem, kteří je posílají ostatním a tak dále. Zatížení distribuce obsahu je distribuován o partnery v cloudu. Partner, který chce přijímat obsah, najde nejbližšího rozdělujícího partnera a získá z nich obsah.

- Distribuce aktualizací produktů

  Síť peer-to-peer může také poskytnout účinný mechanismus distribuce softwaru, jako jsou aktualizace produktů (aktualizace zabezpečení a aktualizace Service Pack). Druhá strana, která má připojení k distribučnímu serveru softwaru, může získat aktualizaci produktu a šířit ji ostatním členům své skupiny.

## <a name="distributed-processing"></a>Distribuované zpracování

- Rozdělení a rozdělení úkolu

  Velký výpočetní úkol lze nejprve rozdělit na samostatné menší výpočetní úlohy, které jsou vhodné pro výpočetní prostředky partnera. Partner by mohl provést rozdělení velké výpočetní úlohy. Potom peer-to-peer sítě můžete distribuovat jednotlivé úkoly samostatné partnery ve skupině. Každý partner provádí svou výpočetní úlohu a hlásí svůj výsledek zpět do centralizovaného bodu akumulace.

- Agregace počítačových prostředků

  Dalším způsobem, jak využít síť peer-to-peer pro distribuované zpracování, je spouštět programy na každém druhém počítači, které běží během doby nečinnosti procesoru a jsou součástí větší výpočetní úlohy, která je koordinována centrálním serverem. Agregací procesorů více počítačů může síť peer-to-peer přeměnit skupinu partnerských počítačů na velký paralelní procesor pro velké výpočetní úlohy.

## <a name="see-also"></a>Viz také

- <xref:System.Net.PeerToPeer.Collaboration>
