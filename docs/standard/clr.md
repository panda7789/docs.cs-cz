---
title: Common Language Runtime (CLR)
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- compiling source code, runtime functionality
- code, execution
- managed data
- runtime
- common language runtime
- metadata, runtime functionality
- .NET Framework, common language runtime
- language compilers
- managed code
- source code execution
- code, runtime functionality
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f465ee77e06255c576146e3e184adede05f5d7bc
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2018
---
# <a name="common-language-runtime-clr"></a>Common Language Runtime (CLR)
Rozhraní .NET Framework poskytuje běhové prostředí volá modul common language runtime, která spustí kód a poskytuje služby, které usnadňují procesu vývoje.  
  
 Kompilátory a nástroje vystavit funkcionalitu modul common language runtime a umožňují napsat kód této výhody z této spravovaného prostředí pro spouštění. Kód, který vyvíjíte pomocí kompilátor jazyka, který se zaměřuje modulu runtime nazývá spravovaný kód. jeho výhody z funkcí, jako je integrace mezi jazyky, mezi jazyky výjimek, lepší zabezpečení, správy verzí a nasazení podporují, jednoduchý model pro interakce komponenty a ladění a profilování služby.  
  
> [!NOTE]
>  Kompilátory a nástroje, se můžou k vytvoření výstupu, který modul common language runtime můžete využívat, protože systém typů formátu metadat a prostředí runtime (systém virtuální provádění) jsou všechny definované veřejný standard společné jazykové ECMA Specifikace infrastruktury. Další informace najdete v tématu [ECMA C# a společné jazykové infrastruktury specifikace](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/).  
  
 Chcete-li povolit modul runtime k poskytování služeb do spravovaného kódu, musí kompilátory jazyka emitování metadata, která popisuje typy, členů a odkazy v kódu. Metadata se ukládají s kódem; Každý načíst běžné language runtime přenosné spustitelného souboru (PE) obsahuje metadata. Modul runtime používá metadata najít a načíst třídy, rozvrhněte instancí v paměti, vyřešit volání metod, generování nativního kódu, vynutit zabezpečení a nastavit kontext spuštění hranice.  
  
 Modul runtime automaticky zpracovává rozložení objektů a spravuje odkazy na objekty používají-li již probíhá. Objekty jejichž existence jsou spravovány tímto způsobem se označují jako spravované data. Uvolňování paměti eliminuje nevracení paměti, jakož i běžné programovací chyby. Pokud váš kód je spravován, můžete data spravované, nespravované data nebo data spravovaných i nespravovaných ve vaší aplikaci rozhraní .NET Framework. Protože kompilátory jazyka zadat své vlastní typy, jako je primitivní typy, může vždy znáte (nebo potřebujete vědět) jestli je spravován vaše data.  
  
 Modul common language runtime snadno součásti návrhu a aplikace, jejichž objekty interakci mezi jazyky. Objekty, které jsou napsané v různých jazycích mohou komunikovat navzájem a jejich chování můžete dají úzce propojit. Můžete například definovat třídu a pak pomocí jazyka odvození třídy z původního třídu nebo volat metodu pro původní třídu. Instance třídy můžete předat také metody třídy napsané v jiném jazyce. Tato integrace mezi jazyky je možné, protože kompilátory jazyka a nástroje, které používají modul runtime použijte obecný systém typů definované modulem runtime a budou se řídí pravidly modul runtime pro definování nových typů, a také pro vytváření, použití a zachování, a Vazba na typy.  
  
 Jako součást jejich metadat provádění všechny spravované součásti informace o součástech a prostředků, které byly vytvořeny. Modul runtime používá tyto informace k zkontrolujte, zda součást nebo aplikace zadaná verze všechny objekty, které potřebuje, takže je méně pravděpodobné, že rozdělit potřebného kódu. Registrační informace a stav data jsou již uloženy v registru, kde může být složité vytvořit a udržovat. Místo toho informace o typy, které definujete (a jejich závislosti) jsou uloženy kódem jako metadata úkoly součást replikace a odebrání mnohem méně složitá.  
  
 Kompilátory jazyka a nástroje vystavit funkcionalitu modulu runtime způsoby, které by měla být užitečné a intuitivní pro vývojáře. To znamená, že některé funkce modulu runtime může být více patrné v jednom prostředí než v jiném. Jak možnosti modulu runtime závisí na které kompilátory jazyka nebo nástroje pro použít. Například pokud jste vývojář jazyka Visual Basic, můžete si všimnout, že se modul common language runtime jazyka Visual Basic má další funkce, než před. Modul runtime poskytuje následující výhody:  
  
-   Vylepšení výkonu.  
  
-   Umožňuje snadno použít součásti vyvinuté v dalších jazycích.  
  
-   Rozšiřitelné typy poskytované knihovny tříd.  
  
-   Jazykové funkce jako je například dědičnosti, rozhraní a přetížení pro objektově orientované programování.  
  
-   Podpora pro explicitní volných vláken, která umožňuje vytvoření s více vlákny škálovatelné aplikace.  
  
-   Podpora pro strukturované zpracování výjimek.  
  
-   Podpora vlastních atributů.  
  
-   Uvolňování paměti.  
  
-   Použití delegátů namísto ukazatelů na funkce pro typ vyšší zabezpečení a zabezpečení. Další informace o delegáti najdete v tématu [obecný systém typů](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="versions-of-the-common-language-runtime"></a>Verze modulu CLR  
 Číslo verze rozhraní .NET Framework neodpovídá nutně číslo verze modulu CLR, které obsahuje. Následující tabulka ukazuje, jak korelovat číslo dvě verze.  
  
|Verze rozhraní .NET Framework|Zahrnuje verze CLR|  
|----------------------------|--------------------------|  
|1.0|1.0|  
|1.1|1.1|  
|2.0|2.0|  
|3.0|2.0|  
|3.5|2.0|  
|4|4|  
|4.5 (včetně 4.5.1 a 4.5.2)|4|  
|4.6 (včetně 4.6.1 a 4.6.2)|4|
|4.7 (včetně 4.7.1)|4|  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Proces spravovaného spuštění](../../docs/standard/managed-execution-process.md)|Popisuje kroky potřebné k využít modul common language runtime.|  
|[Automatická správa paměti](../../docs/standard/automatic-memory-management.md)|Popisuje, jak má systém uvolňování přiděluje a uvolní paměť.|  
|[NIB: Přehled rozhraní .NET Framework](http://msdn.microsoft.com/en-us/ea38ac1e-92af-4d1b-8db1-e8a5ea10ed85)|Popisuje klíčové koncepty rozhraní .NET Framework, např. obecný systém typů, vzájemná funkční spolupráce mezi jazyky, spravovaného spouštění, aplikační domény a sestavení.|  
|[Obecný systém typů](../../docs/standard/base-types/common-type-system.md)|Popisuje, jak jsou typy deklarovat, používat a spravovat v modulu runtime podporu integrace mezi jazyky.|  
  
## <a name="see-also"></a>Viz také  
 [Verze a závislosti](../../docs/framework/migration-guide/versions-and-dependencies.md)
