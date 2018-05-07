---
title: Monolitický aplikace
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: fe25fa8772c60625c5564d5e7194957366a6010a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="monolithic-applications"></a>Monolitický aplikace

V tomto scénáři jsou vytváření jednoho a monolitický webové aplikace nebo služby a jeho nasazení jako kontejner. V aplikaci nemusí být strukturu monolitický; může ho tvoří několik knihovny, komponenty nebo dokonce i vrstvy (aplikační vrstvu, domény vrstvy, vrstva atd.). Externě je jediný kontejner, jako jeden proces, jedné webové aplikace nebo jedné služby.

Ke správě tohoto modelu, můžete nasadit jediný kontejner k reprezentaci aplikace. Pokud chcete použít škálování ho, stačí přidáte pár více kopií pro vyrovnávání zatížení vpředu. Jednoduchost pochází z Správa jedno nasazení v jedné kontejneru nebo virtuální počítač (VM).

Následující objekt, že kontejner jenom jednu funkci a nemá v jednom procesu monolitický vzor je v konfliktu. Můžete přidat více součásti nebo knihovny a interní vrstvy v rámci každý kontejner, jak ukazuje obrázek 4-1.

![](./media/image1.png)

Obrázek 4 – 1: Příklad architektura monolitický aplikace

Nevýhodou tento přístup pochází, nebo když aplikace roste, vyžadování ji škálovat. Pokud bude celá aplikace škálovat, není skutečně problém. Ve většině případů několik součástí aplikace jsou však potlačení body, které vyžadují škálování, zatímco ostatní součásti jsou používány menší.

Použití příklad typické elektronické obchodování, budete pravděpodobně potřebovat je škálovat informace součást produktu. Mnoho zákazníků další Procházet produkty než jejich zakoupení. Další zákazníci využívat nákupního košíku než použití kanálu platba. Méně zákazníky přidání komentářů nebo zobrazit historii jejich nákupu. A pravděpodobně máte jen někteří z nich zaměstnancům, najdete v jedné oblasti, která potřebují spravovat obsah a marketingových kampaní. Škálování monolitický návrhu, všechny kód je nasazenému vícekrát.

Kromě "škálování-všechno" problém, změny jedinou komponentu vyžadují opětovném dokončení testování v celé aplikaci, jakož i úplné nové nasazení všech instancí.

Monolitický přístup je běžné a mnoha organizacích jsou vývoj pomocí této metody architektury. Mnoho získejte vhodné dostatek výsledky, zatímco ostatní dojde k omezení. Mnoho určené svých aplikací v tomto modelu, protože bylo příliš složité sestavení SOAs nástroje a infrastruktura a uvidí nebylo potřeba – dokud vzrostla aplikace.

Z hlediska služby infrastruktury každý server můžete spustit mnoho aplikací v rámci stejného hostitele a mají přijatelné poměr efektivitu vaše využití prostředků, jak je znázorněno na obrázku 4-2.

![](./media/image2.png)

Obrázek 4 – 2: hostitele spuštěných víc aplikací nebo kontejnerů

Monolitický aplikací v Azure můžete nasadit pomocí vyhrazených virtuálních počítačích pro každou instanci. Pomocí [škálovatelné sady virtuálních počítačů Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), je možné snadno škálovat virtuálních počítačů. [Azure App Services](https://azure.microsoft.com/en-us/services/app-service/) můžete spouštět monolitický aplikace a snadno škálovat instance bez nutnosti ke správě virtuálních počítačů. Od 2016 můžete Azure App Services spustit jedné instance Docker kontejnery taky zjednodušuje nasazení. A pomocí Docker, můžete nasadit jeden virtuální počítač jako hostitele Docker a spustit víc instancí. Pomocí Azure vyrovnávání, jak je ukázáno v obrázek 4-3, můžete spravovat škálování.

![](./media/image3.png)

Obrázek 4 – 3: více hostitelů škálování na více systémů jednom Docker aplikace/kontejnery aplikací

Můžete spravovat nasazení na různých hostitelích prostřednictvím techniky tradiční nasazení. Hostitelů Docker můžete spravovat pomocí příkazů jako `docker run` ručně pomocí automatizace, jako je například kanály průběžné doručování (CD), které vám vysvětlíme, dále v této publikaci e.

## <a name="monolithic-application-deployed-as-a-container"></a>Monolitický aplikace nasazena jako kontejner

Existují výhody použití kontejnerů ke správě monolitický nasazení. Změna velikosti instancí kontejnerů je mnohem rychlejší a snadnější než nasazení dalších virtuálních počítačů. I když škálovatelné sady virtuálních počítačů jsou skvělé funkce škálování virtuálních počítačů, které se vyžadují pro hostování Docker kontejnerů, jejich trvat času na vytvoření. Při nasazení jako instance aplikace, je konfigurace aplikace spravované v rámci virtuálního počítače.

Nasazení aktualizací, jako je mnohem rychlejší imagí Dockeru a efektivní sítě. Instance Vn můžete nastavit na stejné hostitelích jako vaše instance Vn-1 odstraňuje přidané náklady vyplývající z dalších virtuálních počítačů. Imagí dockeru obvykle spuštění v sekundách, rychlosti zavedení uživatelům. Zrušení Docker instance je stejně snadná jako vyvolání `docker stop` příkazu, obvykle dokončení menší než za sekundu.

Protože kontejnery jsou ze své podstaty neměnné záměrné, budete muset nikdy starat o poškozená virtuálních počítačů, protože aktualizační skript zapomněli jste na některé specifické konfigurace nebo soubor místu na disku.

I když monolitický aplikace využívat Docker, že dotykové ovládání na pouze tipy výhody. Správa kontejnerů větší výhody pochází z nasazení s orchestrators kontejneru, které spravují různé instance a životní cyklus každá instance kontejneru. Rozdělení monolitický aplikaci do subsystémy, které můžete škálovat, vyvinuté a nasadit jednotlivě je vašim vstupním bodem do sféru mikroslužeb.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Publikování aplikace na jeden kontejner Docker do služby Azure App Service

Buď vzhledem k tomu, že chcete získat rychlý ověření kontejner nasadí do Azure, nebo protože aplikace je jednoduše jedním kontejneru aplikace, aplikační služby Azure nabízí skvělý způsob, jak poskytnout škálovatelných služeb jeden kontejner.

Pomocí služby Azure App Service je intuitivní a můžete zprovoznění a rychle spuštěna, protože poskytuje skvělé Git integrace trvat kódu, sestavení v sadě Microsoft Visual Studio a přímo ji nasadit do Azure. Ale tradičně (s žádné Docker), v případě potřeby další možnosti, architektury nebo závislosti, které nejsou podporované v aplikační služby, je potřeba počkat, dokud tým služby Azure aktualizuje těchto závislostí ve službě App Service nebo přepnout do jiných služeb, třeba Service Fabric, cloudové služby nebo dokonce prostý virtuálních počítačů, pro které máte další ovládací prvek a můžete nainstalovat požadovanou součást nebo framework pro vaši aplikaci.

Nyní, ale (oznamují na Microsoft Connect 2016 v listopadu 2016) a jak ukazuje obrázek 4‑4, pokud používáte Visual Studio 2017, podpora kontejnerů ve službě Azure App Service vám dává možnost zahrnout všechno ve vašem prostředí aplikace. Pokud jste přidali závislost do vaší aplikace, protože běží v kontejneru, získáte možnost včetně těchto závislostí v bitové kopii soubor Docker nebo Docker.

![](./media/image4.png)

Obrázek 4-4: publikování kontejner Azure App Service ze sady Visual Studio. aplikace nebo kontejnery

Obrázek 4 – 4 také ukazuje, že tok publikovat nabízených oznámení bitovou kopii prostřednictvím registru kontejneru, který může být registru kontejner Azure (registr v blízkosti pro vaše nasazení v Azure a zabezpečené účty a skupiny Azure Active Directory) nebo jiné Docker registru jako úložiště Docker Hub nebo místní registrech.


>[!div class="step-by-step"]
[Předchozí] (běžné kontejneru návrhu principles.md) [Další] (state-and-data-in-docker-applications.md)
