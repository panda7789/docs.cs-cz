---
title: Načíst data školení pro tvůrce modelů
description: Naučte se, jak načíst školicí data z SQL Server databáze nebo souboru pro použití v jednom ze scénářů tvůrce modelů pro ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: cc93b3f77284ed283a8d7cbd52b8cd02b4fd9066
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977055"
---
# <a name="load-training-data-into-model-builder"></a>Načtení dat školení do Tvůrce modelů

Naučte se, jak načíst datové sady pro školení ze souboru nebo databáze SQL Server pro použití v jednom ze scénářů tvůrce modelů pro ML.NET. Scénáře tvůrce modelů můžou jako školicí data používat databáze SQL Server, soubory obrázků a formáty souborů CSV nebo TSV.

## <a name="training-dataset-limitations-in-model-builder"></a>Omezení datové sady školení v Tvůrci modelů

Tvůrce modelů omezuje množství a typ dat, která můžete použít pro školicí modely:

- SQL Server data: 100 000 řádků
- Soubory CSV a TSV: bez omezení velikosti
- Obrázky: pouze PNG a JPG.

## <a name="model-builder-scenarios"></a>Scénáře tvůrce modelů

Tvůrce modelů vám pomůže vytvořit modely pro následující scénáře strojového učení:

- Analýza mínění (binární klasifikace): klasifikace textových dat do dvou kategorií.
- Klasifikace problému (klasifikace více tříd): klasifikace textových dat do 3 nebo více kategorií.
- Předpověď ceny (regrese): předpověď číselné hodnoty.
- Klasifikace obrázků (obsáhlý Learning): kategorizace imagí podle vlastností.
- Vlastní scénář: Sestavujte vlastní scénáře z vašich dat pomocí regresí, klasifikace a dalších úkolů.

Tento článek popisuje scénáře klasifikace a regrese s textovými nebo numerickými daty a scénáři klasifikace obrázků.

## <a name="load-text-or-numeric-data-from-a-file"></a>Načtení textu nebo číselných dat ze souboru

Do Tvůrce modelů můžete načíst text nebo číselná data ze souboru. Přijímá formáty souborů ve formátu CSV nebo oddělených tabulátory (TSV).

1. V části datový krok tvůrce modelů vyberte v rozevíracím seznamu zdroj dat možnost **soubor** .
2. Vyberte tlačítko vedle textového pole **Vybrat soubor** a pomocí Průzkumníka souborů Procházejte a vyberte datový soubor.
3. Vyberte kategorii v rozevíracím seznamu **sloupec pro předpověď (popisek)** .
4. V rozevíracím seznamu **vstupní sloupce (funkce)** potvrďte, že jsou zaškrtnuté sloupce dat, které chcete zahrnout.

Pro tvůrce modelů jste dokončili nastavení souboru zdroje dat. Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v Tvůrci modelů.

## <a name="load-data-from-a-sql-server-database"></a>Načtení dat z databáze SQL Server

Tvůrce modelů podporuje načítání dat z místních a vzdálených SQL Serverch databází.

Načtení dat z databáze SQL Server do Tvůrce modulů:

1. V části datový krok tvůrce modelů vyberte v rozevíracím seznamu zdroj dat možnost **SQL Server** .
1. Vyberte tlačítko vedle textového pole **připojit k SQL Server databázi** .
    1. V dialogovém okně **Vybrat data** vyberte **Microsoft SQL Server databázový soubor**.
    1. Zrušte zaškrtnutí políčka **vždy použít tento výběr** a vyberte **pokračovat** .
    1. V dialogovém okně **Vlastnosti připojení** vyberte **Procházet** a vyberte stažený. Soubor MDF.
    1. Vybrat **OK**
1. Z rozevíracího seznamu **název tabulky** vyberte název datové sady.
1. V rozevíracím seznamu **sloupec pro předpověď (popisek)** vyberte kategorii dat, na které chcete vytvořit předpověď.
1. V rozevíracím seznamu **vstupní sloupce (funkce)** potvrďte zaškrtnutí sloupců, které chcete zahrnout.

Pro tvůrce modelů jste dokončili nastavení souboru zdroje dat. Vyberte odkaz **výuka** , který se přesune k dalšímu kroku v Tvůrci modelů.

## <a name="set-up-image-data-files"></a>Nastavení datových souborů obrázků

Tvůrce modelů očekává, že obrazová data budou mít soubory JPG nebo PNG uspořádané ve složkách, které odpovídají kategoriím klasifikace.

Pokud chcete načíst obrázky do Tvůrce modelů, zadejte cestu k jednomu adresáři nejvyšší úrovně:

- Tento adresář nejvyšší úrovně obsahuje jednu podsložku pro každou kategorii, kterou chcete předpovědět.
- Každá podsložka obsahuje soubory obrázků patřící do příslušné kategorie.

V níže uvedené struktuře složek je *flower_photos*adresář nejvyšší úrovně. Existuje pět podadresářů odpovídajících kategoriím, které chcete předpovědět: uzavřené, Dandelion, růže, slunečnice a Tulips. Každý z těchto podadresářů obsahuje obrázky, které patří do příslušné kategorie.

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

Pomocí těchto kurzů sestavíte aplikace Machine Learning pomocí Tvůrce modelů:

- [Předpověď cen pomocí regrese](../tutorials/predict-prices-with-model-builder.md)
- [Analýza mínění ve webové aplikaci pomocí binární klasifikace](../tutorials/sentiment-analysis-model-builder.md )

Pokud model sledujete pomocí kódu, [Naučte se načíst data pomocí rozhraní ml.NET API](load-data-ml-net.md).
