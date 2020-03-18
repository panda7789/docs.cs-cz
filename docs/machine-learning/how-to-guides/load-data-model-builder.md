---
title: Načtení trénovacích dat pro tvůrce modelů
description: Zjistěte, jak načíst trénovací data z databáze serveru SQL Server nebo souboru pro použití v jednom ze scénářů Tvůrce modelů pro ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849156"
---
# <a name="load-training-data-into-model-builder"></a>Načtení dat školení do tvůrce modelů

Zjistěte, jak načíst trénovací datové sady ze souboru nebo databáze serveru SQL Server pro použití v jednom ze scénářů Tvůrce modelů pro ML.NET. Scénáře tvůrce modelů můžete použít SQL Server databáze, obrazové soubory a CSV nebo TSV formáty souborů jako trénovací data.

## <a name="training-dataset-limitations-in-model-builder"></a>Trénování omezení datové sady v Tvůrce modelů

Tvůrce modelů omezuje množství a typ dat, které můžete použít pro trénovací modely:

- Data serveru SQL Server: 100 000 řádků
- Soubory CSV a TSV: Bez omezení velikosti
- Obrázky: Pouze PNG a JPG.

## <a name="model-builder-scenarios"></a>Scénáře tvůrce modelů

Tvůrce modelů vám pomůže vytvořit modely pro následující scénáře strojového učení:

- Analýza mínění (binární klasifikace): Klasifikovat textová data do dvou kategorií.
- Klasifikace problémů (klasifikace více tříd): Klasifikovat textová data do 3 nebo více kategorií.
- Předpověď cen (regrese): Předpovědět číselnou hodnotu.
- Klasifikace obrázků (hluboké učení): Kategorizovat obrázky na základě charakteristik.
- Vlastní scénář: Vytvořte vlastní scénáře z dat pomocí regrese, klasifikace a dalších úkolů.

Tento článek popisuje scénáře klasifikace a regrese s textovými nebo číselnými daty a scénáře klasifikace obrázků.

## <a name="load-text-or-numeric-data-from-a-file"></a>Načtení textových nebo číselných dat ze souboru

Do tvůrce modelů můžete načíst textová nebo číselná data ze souboru. Přijímá formáty souborů csv (oddělené čárkami) nebo tabulátory (TSV).

1. V datovém kroku Tvůrce modelů vyberte **Soubor** z rozevíracího souboru zdroje dat.
2. Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů procházejte a vyberte datový soubor.
3. V rozevíracím seznamu **Sloupec k předvídání (Popisek)** zvolte kategorii.
4. V rozevíracím seznamu **Vstupní sloupce (Funkce)** zkontrolujte, zda jsou zaškrtnuty datové sloupce, které chcete zahrnout.

Dokončení nastavení souboru zdroje dat pro Tvůrce modelů. Vyberte **vlak** odkaz přejít na další krok v Builder.

## <a name="load-data-from-a-sql-server-database"></a>Načtení dat z databáze serveru SQL Server

Tvůrce modelů podporuje načítání dat z místních a vzdálených databází SERVERU SQL Server.

Chcete-li načíst data z databáze serveru SQL Server do tvůrce modulů:

1. V datovém kroku Tvůrce modelů vyberte **SQL Server** z rozevíracího souboru zdroje dat.
1. Vyberte tlačítko vedle textového pole **Připojit k databázi serveru SQL Server.**
    1. V dialogovém okně **Zvolit data** vyberte **položku Microsoft SQL Server Database File**.
    1. Zrušte zaškrtnutí políčka **Vždy použít tento výběr** a vyberte **Pokračovat.**
    1. V dialogovém okně **Vlastnosti připojení** vyberte **Procházet** a vyberte stažený . MDF.
    1. Vybrat **OK**
1. Zvolte název datové sady z rozevíracího souboru **Název tabulky.**
1. V rozevíracím seznamu **Sloupec k předvídání (Popisek)** zvolte kategorii dat, ve které chcete provést předpověď.
1. V rozevíracím seznamu **Vstupní sloupce (Funkce)** zkontrolujte, zda jsou zaškrtnuté sloupce, které chcete zahrnout.

Dokončení nastavení souboru zdroje dat pro Tvůrce modelů. Vyberte **vlak** odkaz přejít na další krok v Builder.

## <a name="set-up-image-data-files"></a>Nastavení datových souborů obrázků

Model Builder očekává, že obrazová data budou soubory JPG nebo PNG uspořádané do složek, které odpovídají kategoriím klasifikace.

Chcete-li načíst obrázky do tvůrce modelů, zadejte cestu k jednomu adresáři nejvyšší úrovně:

- Tento adresář nejvyšší úrovně obsahuje jednu podsložku pro každou z kategorií předpovědět.
- Každá podsložka obsahuje obrazové soubory, které patří do jeho kategorie.

Ve struktuře složek, která je znázorněna níže, je adresář nejvyšší úrovně *flower_photos*. Existuje pět podadresářů odpovídajících kategoriím, které chcete předpovědět: sedmikráska, pampeliška, růže, slunečnice a tulipány. Každý z těchto podadresářů obsahuje obrázky, které patří do jeho příslušné kategorie.

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a>Další kroky

Podle těchto kurzů můžete vytvářet aplikace pro strojové učení pomocí modelového tvůrce:

- [Předvídání cen pomocí regrese](../tutorials/predict-prices-with-model-builder.md)
- [Analýza mínění ve webové aplikaci pomocí binární klasifikace](../tutorials/sentiment-analysis-model-builder.md )

Pokud trénujete model pomocí kódu, [přečtěte si, jak načíst data pomocí ML.NET rozhraní API](load-data-ml-net.md).
