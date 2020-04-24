---
title: .NET Framework – nástroje
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 60a9cb241f289cacc7437174f112114e843aca47
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645568"
---
# <a name="net-framework-tools"></a>.NET Framework – nástroje

Nástroje .NET Framework usnadňují vývoj, nasazení a správu aplikací a komponent určených pro rozhraní .NET Framework.

Většina nástrojů rozhraní .NET Framework popsaná v této části je automaticky nainstalována se sadou Visual Studio. Chcete-li stáhnout Visual Studio, navštivte stránku [Stažení sady Visual Studio.](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

Všechny nástroje můžete spustit z příkazového řádku s výjimkou prohlížeče mezipaměti sestavení (*Shfusion.dll*). Soubor *Shfusion.dll* je nutné získat z Průzkumníka souborů.
  
Nejlepším způsobem, jak spustit nástroje příkazového řádku, je použít příkazový řádek pro vývojáře pro sadu Visual Studio. Tyto nástroje umožňují spustit nástroje snadno, bez přechodu do instalační složky. Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

> [!NOTE]
> Některé nástroje jsou určeny konkrétně pro 32bitové nebo 64bitové počítače. Ujistěte se, že spouštíte příslušnou verzi nástroje pro váš počítač.

## <a name="in-this-section"></a>V tomto oddílu

- [Al.exe (Propojovač sestavení)](al-exe-assembly-linker.md)  
Generuje soubor, který má manifest sestavení z modulů nebo souborů prostředků.

- [Aximp.exe (Import ovládacího prvku ActiveX formulářů systému Windows)](aximp-exe-windows-forms-activex-control-importer.md)  
Převádí definice typů v knihovně typů modelu COM pro ovládací prvek ActiveX na ovládací prvek Windows Forms.

- [Caspol.exe (Nástroj pro zásady zabezpečení přístupu ke kódu)](caspol-exe-code-access-security-policy-tool.md)  
Umožňuje zobrazit a konfigurovat zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad organizace. V rozhraní .NET Framework 4 a novější chod tohoto nástroje nemá vliv na zásady `true`zabezpečení přístupu kódu (CAS), pokud [ \<není nastaven a nenastaven prvek legacyCasPolicy>](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) . Další informace naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

- [Cert2spc.exe (Software Publisher Certificate Test Tool)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Vytvoří certifikát vydavatele softwaru (SPC) z jednoho nebo více certifikátů X.509. Tento nástroj slouží pouze pro účely testování.

- [Certmgr.exe (nástroj správce certifikátů)](certmgr-exe-certificate-manager-tool.md)  
Spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).

- [Clrver.exe (nástroj CLR Version Tool)](clrver-exe-clr-version-tool.md)  
Hlásí všechny nainstalované verze clr (COMMON Language runtime) v počítači.

- [Příkazová zobrazení](developer-command-prompt-for-vs.md)  
Umožňuje snadněji používat nástroje rozhraní .NET Framework. Jedná se o příkazový řádek, který automaticky nastaví specifické proměnné prostředí.

- [CorFlags.exe (Nástroj pro převod CorFlags)](corflags-exe-corflags-conversion-tool.md)  
Dovoluje nastavit CorFlags sekci hlavičky obrazu přenositelného spustitelného souboru (PE).

- [Fuslogvw.exe (prohlížeč protokolů vazby sestavení)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Zobrazuje informace o vazbách sestavení a pomáhá tak diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení za běhu.

- [Gacutil.exe (nástroj globální mezipaměti sestavení)](gacutil-exe-gac-tool.md)  
Dovoluje zobrazit a manipulovat s obsahem globální mezipaměti sestavení a mezipaměti stahování.

- [Ilasm.exe (IL Assembler)](ilasm-exe-il-assembler.md)  
Generuje přenositelný spustitelný soubor (PE) z převodního jazyka (IL; Intermediate Language). Výsledný spustitelný soubor můžete spustit a ověřit tak, že jazyk IL funguje dle očekávání.

- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)  
Zpracovává přenosné spustitelné (PE) soubory obsahující kód jazyka IL a vytváří textový soubor, který může být vstupem do assembleru jazyka IL (Ilasm.exe).

- [Installutil.exe (Instalační nástroj)](installutil-exe-installer-tool.md)  
Dovoluje nainstalovat a odinstalovat prostředky serveru pomocí spuštění instalačních komponent v určeném sestavení. (Pracuje s třídami v oboru <xref:System.Configuration.Install> názvů.)

- [Lc.exe (Kompilátor licencí)](lc-exe-license-compiler.md)  
Čte textové soubory, které obsahují informace o licencích, a vytvoří soubor *.licenses,* který lze vložit do spustitelného souboru s běžným jazykem jako prostředek.

- [Mage.exe (Nástroj pro generování a úpravy manifestu)](mage-exe-manifest-generation-and-editing-tool.md)  
Dovoluje vytvářet, upravovat a podepisovat aplikace a manifesty nasazení. Jako nástroj příkazového řádku lze nástroj *Mage.exe* spustit jak z dávkových skriptů, tak z jiných aplikací založených na systému Windows, včetně ASP.NET aplikací.

- [MageUI.exe (Nástroj pro generování a úpravy manifestu, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Podporuje stejnou funkci jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na Windows. Podporuje stejné funkce jako nástroj příkazového řádku *Mage.exe*, ale používá uživatelské rozhraní (UI) založené na systému Windows.

- [MDbg.exe (Ladicí program příkazového řádku rozhraní .NET Framework)](mdbg-exe.md)  
Pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají modul CLR rozhraní .NET Framework. Tento nástroj používá API ladění za běhu k poskytování služeb ladění.

- [Mgmtclassgen.exe (Management silně typovaný generátor tříd)](mgmtclassgen-exe.md)  
Umožňuje generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI).

- [Mpgo.exe (nástroj pro řízenou optimalizaci profilů)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Umožňuje ladit sestavení nativních bitových kopií pomocí běžných uživatelských scénářů. Mpgo.exe umožňuje generovat a zpracovávat profilovací data pro sestavení aplikací nativních bitových kopií (ne sestavení .NET Framework) použitím tréninkových scénářů vybraných vývojářem aplikace.

- [Ngen.exe (Generátor nativních obrázků)](ngen-exe-native-image-generator.md)  
Zlepšuje výkon spravovaných aplikací použitím nativních bitových kopií (soubory obsahující zkompilovaný strojový kód závislý na procesoru). Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).

- [Peverify.exe (nástroj PEVerify)](peverify-exe-peverify-tool.md)  
Pomáhá ověřit, zda kód MSIL (Microsoft Intermediate Language) a přidružená metadata splňují požadavky na bezpečnost typu.

- [Regasm.exe (nástroj pro registraci shromáždění)](regasm-exe-assembly-registration-tool.md)  
Načte metadata v rámci sestavení a přidá nezbytné položky do registru. To umožňuje klientům modelu COM vypadat jako třídy rozhraní .NET Framework.

- [Regsvcs.exe (Instalační nástroj služby.NET)](regsvcs-exe-net-services-installation-tool.md)  
Načte a zaregistruje sestavení, vygeneruje a nainstaluje knihovny typů do zadané aplikace modelu COM+ verze 1.0 a konfiguruje služby, které jste programově přidali do třídy.

- [Resgen.exe (generátor souborů zdrojů)](resgen-exe-resource-file-generator.md)  
Převede soubory textu (*.txt* nebo *.restext*) a xml-based resource format (*.resx*) soubory na binární soubory běžného modulu runtime (*.resources*), které mohou být vloženy do binárního spustitelného souboru runtime nebo zkompilovány do satelitních sestavení.

- [SecAnnotate.exe (nástroj anotátor zabezpečení.NET)](secannotate-exe-net-security-annotator-tool.md)  
Identifikuje `SecurityCritical` a `SecuritySafeCritical` části sestavy.

- [SignTool.exe (Nástroj pro přihlášení)](signtool-exe.md)  
Digitálně podepisuje soubory, ověřuje podpisy v souborech a opatřuje soubory časovými razítky.

- [Sn.exe (nástroj silný název)](sn-exe-strong-name-tool.md)  
Pomáhá vytvořit sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.

- [SOS.dll (Rozšíření ladění SOS)](sos-dll-sos-debugging-extension.md)  
Pomáhá při ladění spravovaných programů v ladicím programu WinDbg.exe a v sadě Visual Studio poskytováním informací o vnitřním prostředí modulu CLR (Common Language Runtime).

- [SqlMetal.exe (nástroj pro generování kódu)](sqlmetal-exe-code-generation-tool.md)  
Generuje kód a mapování pro technologii LINQ to SQL, která je součástí rozhraní .NET Framework.

- [Storeadm.exe (nástroj izolovaného úložiště)](storeadm-exe-isolated-storage-tool.md)  
Spravuje izolované úložiště a poskytuje možnosti pro výpis uživatelských úložišť a jejich smazání.

- [Tlbexp.exe (Exportér knihovny typů)](tlbexp-exe-type-library-exporter.md)  
Generuje knihovnu typů, které popisují typy definované v sestavení modulu Common Language Runtime.

- [Tlbimp.exe (Importér knihovny typů)](tlbimp-exe-type-library-importer.md)  
Převede definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime.

- [Winmdexp.exe (nástroj pro export metadat modulu Windows Runtime)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
Exportuje sestavení rozhraní .NET Framework, které je zkompilováno jako soubor *.winmdobj,* do součásti prostředí Windows Runtime, která je zabalena jako soubor *.winmd,* který obsahuje metadata prostředí Windows Runtime i informace o implementaci.

- [Winres.exe (Editor prostředků formulářů systému Windows)](winres-exe-windows-forms-resource-editor.md)  
Pomáhá lokalizovat prostředky uživatelského rozhraní *(.resx* nebo *.resources* files), které jsou používány windows forms. Je možné přeložit řetězce a změnit velikost, přesunout a skrýt ovládací prvky pro přizpůsobení lokalizovaných řetězců.

## <a name="related-sections"></a>Související oddíly

- [Nástroje WPF](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
Obsahuje nástroje, jako je nástroj isXPS Conformance (isXPS.exe) a nástroje pro profilování výkonu.

- [Nástroje služby Windows Communication Foundation](../wcf/tools.md)  
Obsahuje nástroje, které usnadňují vytváření, zavádění a správu aplikací služby Windows Communication Foundation (WCF).
