---
title: Proces spravovaného spouštění
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- source code language
- code, managed execution process
- runtime, managed execution process
- compiling source code, managed execution process
- managed execution process
- common language runtime, managed execution process
ms.assetid: 476b03dc-2b12-49a7-b067-41caeaa2f533
ms.openlocfilehash: 0ce7182af33a795188d01ac457b9d45b8ad305dd
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960383"
---
# <a name="managed-execution-process"></a>Proces spravovaného spouštění
<a name="introduction"></a>Proces spravovaného spuštění zahrnuje následující kroky, které jsou podrobně popsány dále v tomto tématu:  
  
1. [Výběr kompilátoru](#choosing_a_compiler).  
  
     Chcete-li získat výhody poskytované modulem CLR (Common Language Runtime), je nutné použít jeden nebo více kompilátorů jazyka, které se zaměřují na modul runtime.  
  
2. [Kompilování kódu do jazyka MSIL](#compiling_to_msil).  
  
     Kompilace převádí zdrojový kód do jazyka MSIL (Microsoft Intermediate Language) a generuje požadovaná metadata.  
  
3. [Kompilování jazyka MSIL do nativního kódu](#compiling_msil_to_native_code).  
  
     V době spuštění přeloží kompilátor JIT (Just-In-Time) jazyk MSIL do nativního kódu. Během této kompilace je nutné, aby kód prošel procesem ověření, který prověří jazyk MSIL a metadata a zjistí, zda kód může být určen jako typově bezpečný.  
  
4. [Spouštění kódu](#running_code).  
  
     Modul CLR (Common Language Runtime) poskytuje infrastrukturu, která umožňuje uskutečnit spuštění a provést služby, které lze použít během spuštění.  
  
<a name="choosing_a_compiler"></a>   
## <a name="choosing-a-compiler"></a>Volba kompilátoru  
 Chcete-li využívat výhod poskytovaných modulem CLR (Common Language Runtime), je nutné použít jeden nebo více kompilátorů jazyka, které se zaměřují na modul runtime, například Visual Basic, C#, Visual C++, F# nebo jeden z mnoha kompilátorů třetích stran, například kompilátor Eiffel, Perl nebo COBOL.  
  
 Vzhledem k tomu, že se jedná o vícejazyčné prostředí pro spouštění, podporuje modul runtime širokou škálu datových typů a vlastností jazyka. Použitý kompilátor jazyka určuje, které vlastnosti modulu runtime jsou k dispozici. Pomocí těchto vlastností pak můžete navrhovat vlastní kód. Váš kompilátor, nikoliv modul runtime, stanovuje syntaxi kódu, kterou musí váš kód používat. Pokud vaše komponenta musí být zcela použitelná komponentami napsanými v jiných jazycích, exportované typy vaší komponenty musí vystavovat pouze jazykové funkce, které jsou zahrnuty v [nezávislosti jazyka a součásti nezávislé na jazyce](../../docs/standard/language-independence-and-language-independent-components.md) (CLS). Můžete použít atribut <xref:System.CLSCompliantAttribute>, chcete-li zajistit, aby kód odpovídal specifikaci CLS. Další informace najdete v tématu [nezávislost jazyka a jazykové komponenty nezávislé na jazyce](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Zpět na začátek](#introduction)  
  
<a name="compiling_to_msil"></a>   
## <a name="compiling-to-msil"></a>Kompilace do jazyka MSIL  
 Při kompilaci spravovaného kódu převádí kompilátor zdrojový kód do jazyka MSIL (Microsoft Intermediate Language), což je sada instrukcí nezávislá na procesoru, které mohou být efektivně převedeny do nativního kódu. Jazyk MSIL obsahuje pokyny pro načítání, ukládání, inicializaci a volání metod na objekty, stejně jako pokyny pro aritmetické a logické operace, tok řízení, přímý přístup do paměti (DMA), zpracování výjimek a jiné operace. Před spuštěním kódu musí být jazyk MSIL převeden na kód specifický pro procesor, obvykle [kompilátorem JIT (just-in-time)](#compiling_msil_to_native_code). Vzhledem k tomu, že modul CLR (Common Language Runtime) poskytuje pro každou podporovanou počítačovou architekturu jeden nebo více kompilátorů JIT, může být stejná sada MSIL zkompilována pomocí kompilátoru JIT a běžet na jakékoliv podporované architektuře.  
  
 Při vytváření jazyka MSIL vytváří kompilátor také metadata. Metadata popisují typy ve vašem kódu, včetně definice každého typu, podpisů členů každého typu, členů, na které odkazuje kód, a dalších dat, která modul runtime používá v době provádění. Jazyk MSIL a metadata jsou obsaženy v přenosném spustitelném souboru (PE), který je založen na publikovaných formátech Microsoft PE a COFF (Common Object File Format) a tyto formáty, jež se v minulosti používaly pro spustitelný obsah, rozšiřuje. Tento formát souboru, který přizpůsobuje jazyk MSIL nebo nativní kód a případně i metadata, umožňuje operačnímu systému rozpoznat bitové kopie modulu CLR (Common Language Runtime). Přítomnost metadat v souboru spolu s jazykem MSIL umožňuje kódu popsat sám sebe, což znamená, že nejsou vyžadovány knihovny typů nebo jazyk IDL (Interface Definition Language). Modul runtime vyhledává a extrahuje metadata ze souboru podle potřeby v průběhu provádění.  
  
 [Zpět na začátek](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>   
## <a name="compiling-msil-to-native-code"></a>Kompilace jazyka MSIL do nativního kódu  
 Před spuštěním jazyka MSIL (Microsoft Intermediate Language) je nutné, aby byl zkompilován proti modulu CLR (Common Language Runtime) do nativního kódu architektury cílového počítače. .NET Framework poskytuje dva způsoby, jak provést tento převod:  
  
- Kompilátor JIT rozhraní .NET Framework.  
  
- .NET Framework [Ngen. exe (generátor nativních imagí)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>Kompilace pomocí kompilátoru JIT  
 Kompilace JIT převede jazyk MSIL do nativního kódu na požádání v době spuštění aplikace, kdy je obsah sestavení načten a proveden. Vzhledem k tomu, že modul CLR (Common Language Runtime) dodává kompilátor JIT pro každou podporovanou architekturu procesoru, mohou vývojáři vytvářet sady sestavení jazyka MSIL, které mohou být zkompilovány při spuštění (JIT) a mohou běžet na různých počítačích s různou architekturou. Nicméně pokud spravovaný kód volá nativní rozhraní API specifická pro konkrétní platformu nebo knihovnu tříd specifickou pro konkrétní platformu, bude kód spuštěn pouze v daném operačním systému.  
  
 Kompilace JIT bere v úvahu možnost, že některý z kódů nemusí být během provádění nikdy volán. Namísto používání času a paměti k převedení všech instrukcí jazyka MSIL v přenosném spustitelném souboru do nativního kódu je během provádění převeden jazyk MSIL podle potřeby a výsledný nativní kód uložen v paměti tak, aby byl přístupný pro pozdější volání v rámci tohoto procesu. Zavaděč vytvoří a připojí zástupnou proceduru ke každé metodě v typu, pokud je typ načten a inicializován. Pokud je metoda volána poprvé, zástupná procedura předá řízení kompilátoru JIT, který převede jazyk MSIL pro danou metodu do nativního kódu a upraví zástupnou proceduru tak, aby odkazovala přímo na generovaný nativní kód. Proto následné volání metody zkompilované JIT přechází přímo na nativní kód.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>Generování kódu pomocí nástroje NGen.exe v době instalace  
 Vzhledem k tomu, že kompilátor JIT převede instrukce jazyka MSIL sestavení do nativního kódu ve chvíli, kdy jsou jednotlivé metody definované v sestavení volány, má tato skutečnost nepříznivý vliv na výkon v době spuštění. Ve většině případů je snížení výkonu přijatelné. Důležitější je, že kód generovaný kompilátorem JIT je vázán na proces, který kompilaci spustil. Nemůže být sdílen napříč více procesy. Aby bylo možné sdílet generovaný kód mezi několika vyvoláními aplikace nebo mezi několika procesy, které sdílejí stejnou množinu sestavení, podporuje modul CLR (Common Language Runtime) režim předčasné kompilace. Tento režim předem používá nástroj [Ngen. exe (generátor nativních bitových kopií)](../../docs/framework/tools/ngen-exe-native-image-generator.md) k převodu sestavení MSIL do nativního kódu, podobně jako kompilátor JIT. Činnost nástroje Ngen.exe se však od kompilátoru JIT liší třemi způsoby:  
  
- Provádí převod z jazyka MSIL do nativního kódu před spuštěním aplikace namísto toho, aby převod uskutečnil, pokud je aplikace spuštěná.  
  
- Kompiluje namísto jedné metody v dané chvíli celé sestavení najednou.  
  
- Uchovává generovaný kód v mezipaměti pro nativní bitové kopie jako soubor na disku.  
  
### <a name="code-verification"></a>Ověření kódu  
 Jako část kompilace do nativního kódu je nutné, aby kód jazyka MSIL absolvoval proces ověření, pokud správce nevytvořil zásady zabezpečení, které umožňují ověření kódu obejít. V rámci ověření se ověřuje jazyk MSIL a metadata a zjišťuje se, zda je kód typově bezpečný, což znamená, že přistupuje pouze k umístěním paměti, k jichž přístupu je oprávněn. Bezpečnost typů pomáhá izolovat objekty od ostatních objektů a pomáhá je chránit před neúmyslným nebo zákeřným poškozením. Zároveň zajišťuje, aby bezpečnostní omezení kódu byla spolehlivě vynucena.  
  
 Modul runtime vychází ze skutečnosti, že následující tvrzení jsou pravdivá pro kód, který je prokazatelně typově bezpečný:  
  
- Odkaz na typ je striktně kompatibilní s odkazovaným typem.  
  
- U objektu jsou vyvolány pouze vhodně definované operace.  
  
- Identity jsou tím, čím dle jejich tvrzení jsou.  
  
 Během procesu ověřování je kód jazyka MSIL kontrolován, aby bylo možné potvrdit, že kód může přistupovat k oblastem paměti a volat metody pouze prostřednictvím správně definovaných typů. Kód například nemůže povolit polím objektu, aby byla přístupná takovým způsobem, který umožňuje přetečení oblastí paměti. Navíc se v rámci ověření provádí kontrola kódu za účelem zjištění, zda byl kód jazyka MSIL správně vygenerován, protože nesprávný kód jazyka MSIL může vést k narušení pravidel bezpečnosti typu. Proces ověřování zkoumá přesně definovanou sadu typově bezpečných kódů a předává pouze typově bezpečný kód. Některé typově bezpečné kódy však nemusí ověření absolvovat úspěšně z důvodu určitých omezení procesu ověřování a některé jazyky pak záměrně neprodukují kód, který je prokazatelně typově bezpečný. Pokud je typově bezpečný kód vyžadován zásadami zabezpečení, avšak není úspěšně ověřen, bude při spuštění kódu vyvolána výjimka.  
  
 [Zpět na začátek](#introduction)  
  
<a name="running_code"></a>   
## <a name="running-code"></a>Spuštění kódu  
 Modul CLR (Common Language Runtime) poskytuje infrastrukturu, která umožňuje uskutečnit spravované spuštění a služby, jež lze použít během provádění. Před spuštěním metody je nutné, aby byla zkompilována do kódu specifického pro procesor. Jednotlivé metody, pro které byl vygenerován kód jazyka MSIL, jsou při prvním volání kompilovány pomocí kompilátoru JIT a poté spuštěny. Jakmile příště metodu spustíte, spustí se stávající nativní kód zkompilovaný pomocí kompilátoru JIT. Proces kompilace JIT a následné spuštění kódu se opakuje až do dokončení provádění.  
  
 Během provádění obdrží spravovaný kód služby, jako je například uvolňování paměti, zabezpečení, spolupráce s nespravovaným kódem, podpora ladění mezi jazyky, vylepšené nasazení a podpora správy verzí.  
  
 V systému Microsoft Windows Vista zavaděč operačního systému kontroluje spravované moduly prozkoumáním bitu v hlavičce COFF. Nastavený bit označuje spravovaný modul. Pokud zavaděč odhalí spravované moduly, načte soubor mscoree.dll a poté `_CorValidateImage` nebo `_CorImageUnloading` upozorní zavaděč ve chvíli, kdy jsou bitové kopie spravovaného modulu načteny nebo uvolněny. `_CorValidateImage` provádí následující akce:  
  
1. Zajistí, aby byl kód platným spravovaným kódem.  
  
2. Změní vstupní bod v bitové kopii na vstupní bod v modulu runtime.  
  
 V 64bitovém systému Windows upraví `_CorValidateImage` bitovou kopii uloženou v paměti její transformací z formátu PE32 na formát PE32+.  
  
 [Zpět na začátek](#introduction)  
  
## <a name="see-also"></a>Viz také:

- [Přehled](../../docs/framework/get-started/overview.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../docs/standard/language-independence-and-language-independent-components.md)
- [Metadata a komponenty popisující samy sebe](../../docs/standard/metadata-and-self-describing-components.md)
- [Ilasm.exe (IL Assembler)](../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Zabezpečení](../../docs/standard/security/index.md)
- [Spolupráce s nespravovaným kódem](../../docs/framework/interop/index.md)
- [Nasazení](../../docs/framework/deployment/net-framework-applications.md)
- [Sestavení v .NET](assembly/index.md)
- [Aplikační domény](../../docs/framework/app-domains/application-domains.md)
