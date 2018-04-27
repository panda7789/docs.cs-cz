---
title: Návrh výčtu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3e89567761367ddcd67078b138c15b982a0d666
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="enum-design"></a>Návrh výčtu
Výčty jsou zvláštní druh typ hodnoty. Existují dva druhy výčty: jednoduchý výčty a příznak výčty.  
  
 Jednoduché výčty představují malé uzavřené sady možností. Běžným příkladem je jednoduchý výčet je sada barev.  
  
 Příznak výčty jsou navrženy pro podporu bitové operace na hodnoty výčtu. Běžným příkladem je výčet příznaků je seznam možností.  
  
 **PROVEĎTE ✓** pomocí výčet parametry, vlastnosti, silného typu a návratové hodnoty, které představují sadu hodnot.  
  
 **PROVEĎTE ✓** upřednostnit pomocí výčet místo statické konstanty.  
  
 **X nesmí** používat výčet pro otevřené sady (například verzi operačního systému, názvy přátel, atd.).  
  
 **X nesmí** poskytují vyhrazené výčet hodnot, které jsou určené pro budoucí použití.  
  
 Vždy jednoduše přidáním hodnoty do existující výčtu v pozdější fázi. V tématu [přidání hodnoty výčty](#add_value) Další informace o přidání hodnot do výčty. Vyhrazené hodnoty právě znečištění směrovány správu sadu skutečné hodnoty a vede k chyby uživatele.  
  
 **X nepoužívejte** veřejně vystavení výčty pomocí pouze jednu hodnotu.  
  
 Běžnou praxí pro zajištění budoucí rozšíření rozhraní API jazyka C je přidání vyhrazené parametrů do metoda signatur. Takové vyhrazené parametry může být vyjádřený jako výčty pomocí jednoho výchozí hodnotu. To by neměl spravované rozhraní API. Přetěžování metody umožňuje přidání parametrů v budoucích vezích se.  
  
 **X nesmí** zahrnout sentinel hodnoty výčty.  
  
 I když jsou někdy jsou užitečné pro vývojáře framework, sentinel hodnoty jsou pro uživatele Framework matoucí. Používají se ke sledování stavu vrácení, jedna z hodnot výčtu spíše než ze sady reprezentována výčtového typu.  
  
 **PROVEĎTE ✓** zadejte hodnotu nula na jednoduchý výčty.  
  
 Zvažte možnost volání hodnota něco podobného jako "None." Pokud tuto hodnotu není vhodná pro tento konkrétní výčet, je vhodné nejběžnější výchozí hodnota pro výčet přiřadit základní hodnota nula.  
  
 **✓ ZVAŽTE** pomocí <xref:System.Int32> (výchozí ve většině programovacích jazycích) jako nadřazený typ enum Pokud žádné z následujících:  
  
-   Je výčet je výčet příznaků a máte víc než 32 příznaky, nebo se očekávají, že mají více v budoucnu.  
  
-   Základní typ musí být jiný než <xref:System.Int32> jednodušší funkční spolupráce s nespravovaným kódem očekává jinou velikost výčty.  
  
-   Menší podkladovým typem by způsobilo významné úspory v prostoru. Pokud očekáváte výčtu, která má být použit především jako argument pro tok řízení, velikost způsobuje malé rozdíly. Úspora velikosti může být důležité pokud:  
  
    -   Očekáváte výčtu, která má být použit jako pole v velmi často instancí struktura nebo třída.  
  
    -   Očekáváte uživatelům vytvářet velké pole nebo kolekce výčet instancí.  
  
    -   Očekáváte velký počet instancí výčtu k serializaci.  
  
 Pro použití v paměti, uvědomte si, že spravované objekty jsou vždy `DWORD`-zarovnán, proto musíte efektivně více výčty nebo jiné malé struktury v instanci do pack menší výčtu s aby rozdíl, protože velikost celkový instance je vždy má být zaokrouhlené nahoru `DWORD`.  
  
 **PROVEĎTE ✓** název příznak výčty pomocí množném čísle podstatná jména či fráze podstatné jméno a jednoduchý výčty pomocí singulární podstatná jména či fráze podstatné jméno.  
  
 **X nesmí** rozšířit <xref:System.Enum?displayProperty=nameWithType> přímo.  
  
 <xref:System.Enum?displayProperty=nameWithType> je speciální typ používaný službou modulu CLR vytvořit uživateli definované výčty. Většina programovacích jazyků zadejte programovací element, který umožňuje přístup k této funkce. Například v jazyce C# `enum` – klíčové slovo se používá k definování výčet.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Návrh příznak výčty  
 **PROVEĎTE ✓** použít <xref:System.FlagsAttribute?displayProperty=nameWithType> na příznak výčty. Tento atribut nevztahují na jednoduchý výčty.  
  
 **PROVEĎTE ✓** použít zajišťuje dva pro hodnoty výčtu příznak, mohou být volně kombinovány pomocí bitové operace OR.  
  
 **✓ ZVAŽTE** poskytování hodnot speciální výčtu pro běžně používá kombinace příznaků.  
  
 Bitové operace jsou rozšířené koncept a nesmí být požadovány pro jednoduché úlohy. <xref:System.IO.FileAccess.ReadWrite> je příklad speciální hodnoty.  
  
 **X nepoužívejte** vytváření výčtů příznak, kde jsou neplatné určité kombinace hodnot.  
  
 **X nepoužívejte** pomocí příznak hodnoty výčtu nula, pokud hodnota představuje "všechny příznaky jsou vymazány" a je správně podle další obecné zásady s názvem.  
  
 **PROVEĎTE ✓** název nulové hodnoty příznak výčtů `None`. Pro příkaz enum příznak musí hodnota vždy význam "všechny příznaky jsou vymazány."  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Přidáním hodnoty pro výčty  
 Je velmi běžné ke zjištění, budete muset po jste již odeslali ho přidat hodnoty výčtu. Potenciální problémy s kompatibilitou aplikací Pokud nastane je vrácena hodnota nově přidané z existujícího rozhraní API, protože chybně napsané aplikace nemusí správně zpracovat novou hodnotu.  
  
 **✓ ZVAŽTE** přidání hodnot do výčty navzdory riziko malé kompatibility.  
  
 Pokud máte reálná data o aplikace nekompatibility způsobené doplňky výčet, zvažte přidání nového rozhraní API, který vrací hodnoty novém i starém a přestat používat staré rozhraní API, které by měly pokračovat ve vrací pouze původní hodnoty. Tím bude zajištěno, že zůstanou existující aplikace kompatibilní.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
