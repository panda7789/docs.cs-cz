---
title: .NET Framework – nástroje
description: Podívejte se na seznam nástrojů .NET, které usnadňují vytváření, nasazování a správu aplikací a komponent cílících na rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 0a5cbcd4fa60b819d3ab07a4f221e77ca106c321
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166850"
---
# <a name="net-framework-tools"></a>.NET Framework – nástroje

Nástroje .NET Framework usnadňují vývoj, nasazení a správu aplikací a komponent určených pro rozhraní .NET Framework.

Většina nástrojů rozhraní .NET Framework popsaná v této části je automaticky nainstalována se sadou Visual Studio. Pokud si chcete stáhnout Visual Studio, přejděte na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .

Všechny nástroje můžete spustit z příkazového řádku s výjimkou rozhraní Assembly Cache Viewer (*Shfusion.dll*). Musíte mít přístup k *Shfusion.dll* z Průzkumníka souborů.
  
Nejlepším způsobem, jak spustit nástroje příkazového řádku, je použít příkazový řádek pro vývojáře pro sadu Visual Studio. Tyto nástroje umožňují spustit nástroje snadno, bez přechodu do instalační složky. Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

> [!NOTE]
> Některé nástroje jsou určeny konkrétně pro 32bitové nebo 64bitové počítače. Ujistěte se, že spouštíte příslušnou verzi nástroje pro váš počítač.

## <a name="in-this-section"></a>V této části

- [Al.exe (linker sestavení)](al-exe-assembly-linker.md)  
Generuje soubor, který má manifest sestavení z modulů nebo souborů prostředků.

- [Aximp.exe (import ovládacího prvku ActiveX model Windows Forms)](aximp-exe-windows-forms-activex-control-importer.md)  
Převádí definice typů v knihovně typů modelu COM pro ovládací prvek ActiveX na ovládací prvek Windows Forms.

- [Caspol.exe (nástroj zásady zabezpečení přístupu kódu)](caspol-exe-code-access-security-policy-tool.md)  
Umožňuje zobrazit a konfigurovat zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad organizace. V .NET Framework 4 nebo novějším tento nástroj nemá vliv na zásady zabezpečení přístupu kódu (CAS), pokud není [ \<legacyCasPolicy> element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) nastaven na `true` . Další informace najdete v tématu [změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).

- [Cert2spc.exe (Nástroj pro testování certifikátu vydavatele softwaru)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Vytvoří certifikát vydavatele softwaru (SPC) z jednoho nebo více certifikátů X.509. Tento nástroj slouží pouze pro účely testování.

- [Certmgr.exe (nástroj Správce certifikátů)](certmgr-exe-certificate-manager-tool.md)  
Spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).

- [Clrver.exe (nástroj verze CLR)](clrver-exe-clr-version-tool.md)  
Oznamuje všechny nainstalované verze modulu CLR (Common Language Runtime) v počítači.

- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)  
Umožňuje snadnější použití .NET Framework nástrojů. Jedná se o příkazový řádek, který automaticky nastaví konkrétní proměnné prostředí.

- [CorFlags.exe (Nástroj pro převod CorFlags)](corflags-exe-corflags-conversion-tool.md)  
Dovoluje nastavit CorFlags sekci hlavičky obrazu přenositelného spustitelného souboru (PE).

- [Fuslogvw.exe (Prohlížeč protokolu vazby sestavení)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Zobrazuje informace o vazbách sestavení a pomáhá tak diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení za běhu.

- [Gacutil.exe (nástroj Global Assembly Cache Tool)](gacutil-exe-gac-tool.md)  
Dovoluje zobrazit a manipulovat s obsahem globální mezipaměti sestavení a mezipaměti stahování.

- [Ilasm.exe (IL Assembler)](ilasm-exe-il-assembler.md)  
Generuje přenositelný spustitelný soubor (PE) z převodního jazyka (IL; Intermediate Language). Výsledný spustitelný soubor můžete spustit a ověřit tak, že jazyk IL funguje dle očekávání.

- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)  
Zpracovává přenosné spustitelné (PE) soubory obsahující kód jazyka IL a vytváří textový soubor, který může být vstupem do assembleru jazyka IL (Ilasm.exe).

- [Installutil.exe (nástroj Installer Tool)](installutil-exe-installer-tool.md)  
Dovoluje nainstalovat a odinstalovat prostředky serveru pomocí spuštění instalačních komponent v určeném sestavení. (Funguje se třídami v <xref:System.Configuration.Install> oboru názvů.)

- [Lc.exe (kompilátor licencí)](lc-exe-license-compiler.md)  
Přečte textové soubory, které obsahují informace o licencování a vytvoří soubor *. licenses* , který může být vložen do spustitelného souboru modulu CLR jako prostředek.

- [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md)  
Dovoluje vytvářet, upravovat a podepisovat aplikace a manifesty nasazení. Jako nástroj příkazového řádku můžete *Mage.exe* spustit z skriptů Batch i jiných aplikací pro Windows, včetně aplikací ASP.NET.

- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Podporuje stejnou funkci jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na Windows. Podporuje stejné funkce jako nástroj příkazového řádku *Mage.exe*, ale používá uživatelské rozhraní (UI) založené na systému Windows.

- [MDbg.exe (ladicí program příkazového řádku .NET Framework)](mdbg-exe.md)  
Pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají modul CLR rozhraní .NET Framework. Tento nástroj používá API ladění za běhu k poskytování služeb ladění.

- [Mgmtclassgen.exe (generátor tříd se silnými typy správy)](mgmtclassgen-exe.md)  
Umožňuje generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI).

- [Mpgo.exe (Nástroj pro optimalizaci spravovaného profilu)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Umožňuje ladit sestavení nativních bitových kopií pomocí běžných uživatelských scénářů. Mpgo.exe umožňuje generovat a zpracovávat profilovací data pro sestavení aplikací nativních bitových kopií (ne sestavení .NET Framework) použitím tréninkových scénářů vybraných vývojářem aplikace.

- [Ngen.exe (generátor nativních imagí)](ngen-exe-native-image-generator.md)  
Zlepšuje výkon spravovaných aplikací použitím nativních bitových kopií (soubory obsahující zkompilovaný strojový kód závislý na procesoru). Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).

- [Peverify.exe (nástroj Nástroj PEVerify)](peverify-exe-peverify-tool.md)  
Pomáhá ověřit, zda kód MSIL (Microsoft Intermediate Language) a přidružená metadata splňují požadavky na bezpečnost typu.

- [Regasm.exe (nástroj registrace sestavení)](regasm-exe-assembly-registration-tool.md)  
Načte metadata v rámci sestavení a přidá nezbytné položky do registru. To umožňuje klientům modelu COM vypadat jako třídy rozhraní .NET Framework.

- [Regsvcs.exe (Nástroj pro instalaci služeb .NET)](regsvcs-exe-net-services-installation-tool.md)  
Načte a zaregistruje sestavení, vygeneruje a nainstaluje knihovny typů do zadané aplikace modelu COM+ verze 1.0 a konfiguruje služby, které jste programově přidali do třídy.

- [Resgen.exe (generátor zdrojového souboru)](resgen-exe-resource-file-generator.md)  
Převede soubory textu (*. txt* nebo *. restext*) a souborů formátu prostředků založených na jazyce XML (*. resx*) na binární soubory modulu CLR (*. Resources*), které mohou být vloženy do binárního spustitelného souboru modulu runtime nebo kompilovány do satelitních sestavení.

- [SecAnnotate.exe (nástroj bezpečnostní anotace .NET)](secannotate-exe-net-security-annotator-tool.md)  
Identifikuje `SecurityCritical` části a v `SecuritySafeCritical` sestavení.

- [SignTool.exe (nástroj Sign Tool)](signtool-exe.md)  
Digitálně podepisuje soubory, ověřuje podpisy v souborech a opatřuje soubory časovými razítky.

- [Sn.exe (Nástroj pro silný název)](sn-exe-strong-name-tool.md)  
Pomáhá vytvořit sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.

- [SOS.dll (rozšíření ladění SOS)](sos-dll-sos-debugging-extension.md)  
Pomáhá při ladění spravovaných programů v ladicím programu WinDbg.exe a v sadě Visual Studio poskytováním informací o vnitřním prostředí modulu CLR (Common Language Runtime).

- [SqlMetal.exe (Nástroj pro generování kódu)](sqlmetal-exe-code-generation-tool.md)  
Generuje kód a mapování pro technologii LINQ to SQL, která je součástí rozhraní .NET Framework.

- [Storeadm.exe (Nástroj izolovaného úložiště)](storeadm-exe-isolated-storage-tool.md)  
Spravuje izolované úložiště a poskytuje možnosti pro výpis uživatelských úložišť a jejich smazání.

- [Tlbexp.exe (typ Exportér knihovny)](tlbexp-exe-type-library-exporter.md)  
Generuje knihovnu typů, které popisují typy definované v sestavení modulu Common Language Runtime.

- [Tlbimp.exe (importér knihovny typů)](tlbimp-exe-type-library-importer.md)  
Převede definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime.

- [Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
Exportuje sestavení .NET Framework, které je kompilováno jako soubor *. winmdobj* , do komponenty prostředí Windows Runtime, která je zabalena jako soubor *. winmd* , který obsahuje prostředí Windows Runtime metadata i informace o implementaci.

- [Winres.exe (editor prostředků model Windows Forms)](winres-exe-windows-forms-resource-editor.md)  
Pomáhá lokalizovat prostředky uživatelského rozhraní (soubory *. resx* nebo *. Resources* ), které jsou používány model Windows Forms. Je možné přeložit řetězce a změnit velikost, přesunout a skrýt ovládací prvky pro přizpůsobení lokalizovaných řetězců.

## <a name="related-sections"></a>Související oddíly

- [WPF – nástroje](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
Obsahuje nástroje, jako je isXPS (isXPS.exe) a nástroje pro profilaci výkonu.

- [Nástroje služby Windows Communication Foundation](../wcf/tools.md)  
Obsahuje nástroje, které usnadňují vytváření, zavádění a správu aplikací služby Windows Communication Foundation (WCF).
