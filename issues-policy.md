---
ms.openlocfilehash: 33178637c4fcfb21e8190c3d2593f09326ea5995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73554846"
---
# <a name="github-issues-process-and-policy"></a>GitHub vydává proces a zásady

Cílem tohoto procesu jsou:

1. Zajistěte, aby chyby nebo opomenutí v našich dokumentech neblokovaly úspěch zákazníků.
1. Buďte citliví na zpětnou vazbu a obavy zákazníků.
1. Neustále zlepšovat zákaznickou zkušenost.
1. Další informace o zkušenostech zákazníků najdete v otevřeném dialogu o výzvách a řešeních.

Proces používá dvě fáze k zajištění odezvy při stanovení priorit práce. Počáteční fáze diagnostikuje a tají problém. Druhá fáze řeší problém. Je-li problém snadný a naléhavý, mohou být obě fáze kombinovány.

Proces zahrnuje úkoly s pevným časovým přidělením:

- Každý člen týmu stráví každý pracovní den až 1/2 hodiny [klasifikací příchozích problémů](#diagnosis-phase)včetně počátečních odpovědí. Tím je zajištěno, že reagujeme na nové problémy.
- Každý člen týmu stráví až 1/2 dne [týdně aktualizací dokumentů,](#resolution-phase) aby vyřešil problémy githubu generovaným zákazníkem.

## <a name="diagnosis-phase"></a>Diagnostická fáze

Každý člen týmu stráví až 30 minut za pracovní den kategorizací nových problémů. Odpovídáme na následující otázky:

- Je problém docs problém nebo problém s produktem?
- Není to problém, ale otázka vhodnější pro fórum nebo podporu webu?
- Jakou prioritu má otázka?
- Která oblast tento problém spravuje?

Pokud tyto otázky nemohou být zodpovězeny v počátečním vyšetření, klademe objasňující otázky v komentářích.

Existují typy problémů, které jsou uzavřeny během fáze diagnostiky a třídění:

- **sláva**: Vyjadřujeme díky, a uzavřít problém.
- **Problém s produktem**: Problémy související s produktem a nikoli s jeho dokumentací jsou uzavřeny. Můžeme také podniknout další kroky, jak je popsáno níže.
- **Porušení kodexu :** Tyto problémy jsou uzavřeny a hlášeny, pokud [porušení kodexu si](https://dotnetfoundation.org/code-of-conduct) zaslouží nahlášení a blokování.
- **Duplikáty**: Duplikáty jsou uzavřeny s komentářem odkazujícím na existující problém.
- **doc-ok**: Zákazník je nesprávný a doc je správný.
- **fórum**: Problémy, které jsou požadavky na podporu nebo fórum, jsou směrovány na přetečení zásobníku nebo jiné weby podpory a uzavřeny.

### <a name="actions-on-product-issues"></a>Akce týkající se problémů s produkty

V závislosti na povaze problému s produktem se můžeme rozhodnout:

- Přeneste problém do příslušného úložiště produktů.
- Zavřete problém jako duplikát existujících požadavků na produkt.
- Problém můžete uzavřít doporučením k otevření v úložišti produktů.

Hodnocení správného postupu je subjektivní. Členové týmu používají svůj úsudek o správném postupu.

### <a name="actions-on-content-issues"></a>Akce týkající se problémů s obsahem

Pro další otázky, tým:

- Přiřadí prioritu
- Přiřadí milník, obvykle "Nevyřízené položky"
- Vyhodnotí, zda je problém dobrým problémem "k mání" nebo [projekty pro přispěvatele komunity .NET](https://github.com/dotnet/docs/projects/35)

Úrovně priority jsou založeny na následujících pokynech, ale jsou subjektivní. Milníky jsou také subjektivní a jsou založeny na dalších prioritách, jako jsou aktuální plány vydání produktu a nadcházející uvedení na trh.

- **P0**: Docs opomenutí nebo chyba zabraňuje zákazníkům v úspěšném v běžném scénáři.
  - **Problémy P0** jsou řešeny během příštích tří týdnů, přičemž přednost před dříve naplánované práce.
- **P1**: Docs opomenutí nebo chyba je běžný scénář mnohem těžší nebo blokuje jiné známé scénáře.
  - **Problémy P1** jsou naplánovány včas. Problémy P1 jsou často plánovány na nadcházející milník.
- **P2**: Problémy, které způsobují drobné nepříjemnosti nebo ovlivňují článek o zobrazení nízké stránky.
  - **Problémy P2** jsou obecně opraveny při aktualizaci článku z důvodů s vyšší prioritou.
- **P3**: Problémy, které jsou požadavky na scénáře případu edge.
  - **P3** problémy jsou umístěny v nevyřízených položkách a jsou považovány za aktualizace při aktualizaci článků z důvodů s vyšší prioritou.

Členové týmu tráví omezenou dobu na diagnózu a třídění, aby mohli pokročit v naplánovaných úkolech. Každý člen týmu stráví maximálně 30 minut denně v diagnostice a třídění.

Štítek **up-for-grabs** se použije, když je problém dobrým kandidátem pro člena komunity (případně autora) k odeslání opravy. Člen týmu, který použije štítek **up-for-grabs,** pomůže nebo najde někoho, kdo pomůže členům komunity pracovat prostřednictvím procesu vytváření PR. Otázky, které jsou "k mání", jsou často přidávány do [projektů příspěvku Společenství](https://github.com/dotnet/docs/projects/35)

> Poznámka: Teprve nedávno jsme přijali předchozí konvence. Osoba, která přidala štítek, vás může odkázat na jiného člena týmu, který vám pomůže.

## <a name="resolution-phase"></a>Fáze řešení

Problémy generované zákazníkem jsou váženy jako součást plánování naplánovaných úkolů. Každý člen týmu přiděluje 4 hodiny týdně k řešení problémů zákazníků s nejvyšší prioritou.

Řešení problémů vyplývá z úrovně priority nastavené během diagnostiky. Problémy příchozích zákazníků jsou upřednostňovány s dalšími plánovanými pracemi s podobnou prioritou

- **P0**: Jakmile je to rozumné, během příštích tří týdnů.
- **P1**: Naplánováno s dalšími plánovanými pracemi P1. To obvykle znamená, že v příštích třech měsících.
- **P2**: Naplánováno s dalšími plánovanými p2 pracemi. P2 otázky jsou naplánovány pravidelně na základě oblasti a viditelnosti. Častěji budou problémy P2 vyřešeny při aktualizaci článku.
- **P3**: Žádná záruka v den opravy. Při aktualizaci článku, prověříme nevyřízené položky pro další problémy na stejném článku.

Problémy mohou být repriorityd na základě nové zpětné vazby a data o viditelnostčlánku.
