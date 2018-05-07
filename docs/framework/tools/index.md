---
title: .NET Framework – nástroje
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65614d906abc2dec5dc5891b16b595cf9ef9d56f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="net-framework-tools"></a>.NET Framework – nástroje
Nástroje .NET Framework usnadňují vývoj, nasazení a správu aplikací a komponent určených pro rozhraní .NET Framework.  
  
 Většina nástrojů rozhraní .NET Framework popsaná v této části je automaticky nainstalována se sadou Visual Studio. (Informace o instalaci, najdete v článku [Visual Studio stáhne](http://go.microsoft.com/fwlink/?LinkID=325532).)  
  
 Veškeré nástroje, s výjimkou nástroje Assembly Cache Viewer (Shfusion.dll), lze spustit z příkazového řádku. K nástroji Shfusion.dll je nutné získat přístup z Průzkumníku souborů.  
  
 Nejlepším způsobem, jak spustit nástroje příkazového řádku, je použít příkazový řádek pro vývojáře pro sadu Visual Studio. Tyto nástroje umožňují spustit nástroje snadno, bez přechodu do instalační složky. Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Některé nástroje jsou určeny konkrétně pro 32bitové nebo 64bitové počítače. Ujistěte se, že spouštíte příslušnou verzi nástroje pro váš počítač.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Al.exe (linker sestavení)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 Generuje soubor, který má manifest sestavení z modulů nebo souborů prostředků.  
  
 [Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)](../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 Převádí definice typů v knihovně typů modelu COM pro ovládací prvek ActiveX na ovládací prvek Windows Forms.  
  
 [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)  
 Umožňuje zobrazit a konfigurovat zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad organizace. V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] a novější, tento nástroj neovlivní zásady (CAS) zabezpečení přístupu kódu, pokud [ \<legacyCasPolicy > element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) je nastaven na `true`. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 [Cert2spc.exe (nástroj pro testování certifikátu vydavatele softwaru)](../../../docs/framework/tools/cert2spc-exe-software-publisher-certificate-test-tool.md)  
 Vytvoří certifikát vydavatele softwaru (SPC) z jednoho nebo více certifikátů X.509. Tento nástroj slouží pouze pro účely testování.  
  
 [Certmgr.exe (nástroj Certificate Manager)](../../../docs/framework/tools/certmgr-exe-certificate-manager-tool.md)  
 Spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).  
  
 [Clrver.exe (nástroj verze CLR)](../../../docs/framework/tools/clrver-exe-clr-version-tool.md)  
 sestavy nainstalovaných verzí common language runtime (CLR) v počítači.  
  
 [CorFlags.exe (CorFlags – převodní nástroj)](../../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)  
 Dovoluje nastavit CorFlags sekci hlavičky obrazu přenositelného spustitelného souboru (PE).  
  
 [Fuslogvw.exe (prohlížeč protokolu vazby sestavení)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)  
 Zobrazuje informace o vazbách sestavení a pomáhá tak diagnostikovat, proč rozhraní .NET Framework nemůže najít sestavení za běhu.  
  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 Dovoluje zobrazit a manipulovat s obsahem globální mezipaměti sestavení a mezipaměti stahování.  
  
 [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 Generuje přenositelný spustitelný soubor (PE) z převodního jazyka (IL; Intermediate Language). Výsledný spustitelný soubor můžete spustit a ověřit tak, že jazyk IL funguje dle očekávání.  
  
 [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 Zpracovává přenosné spustitelné (PE) soubory obsahující kód jazyka IL a vytváří textový soubor, který může být vstupem do assembleru jazyka IL (Ilasm.exe).  
  
 [Installutil.exe (instalační nástroj)](../../../docs/framework/tools/installutil-exe-installer-tool.md)  
 Dovoluje nainstalovat a odinstalovat prostředky serveru pomocí spuštění instalačních komponent v určeném sestavení. (Funguje s třídami v <xref:System.Configuration.Install> oboru názvů.) Dovoluje nainstalovat a odinstalovat prostředky serveru pomocí spuštění instalačních komponent v určeném sestavení. (Funguje s třídami v <xref:System.Configuration.Install> oboru názvů.)  
  
 [Lc.exe (kompilátor licencí)](../../../docs/framework/tools/lc-exe-license-compiler.md)  
 Čte textové soubory obsahující licenční informace a vytváří soubor .licenses, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime). Čte textové soubory obsahující licenční informace a vytváří soubor .licenses, který může být integrován jako prostředek do spustitelného souboru modulu CLR (Common Language Runtime).  
  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 Dovoluje vytvářet, upravovat a podepisovat aplikace a manifesty nasazení. Jakožto nástroj příkazového řádku lze nástroj Mage.exe spouštět z dávkových skriptů a jiných aplikací pro systém Windows, včetně aplikací ASP.NET.  
  
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 Podporuje stejnou funkci jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na Windows. Podporuje stejnou funkci jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na Windows.  
  
 [MDbg.exe (ladicí program z příkazového řádku .NET Framework)](../../../docs/framework/tools/mdbg-exe.md)  
 Pomáhá výrobcům nástrojů a vývojářům aplikací najít a opravit chyby v programech, které využívají modul CLR rozhraní .NET Framework. Tento nástroj používá API ladění za běhu k poskytování služeb ladění.  
  
 [Mgmtclassgen.exe (spravovaný generátor tříd se silnými typy)](../../../docs/framework/tools/mgmtclassgen-exe.md)  
 Umožňuje generovat spravovanou třídu s časnou vazbou pro zadanou třídu Windows Management Instrumentation (WMI).  
  
 [Mpgo.exe (Nástroj pro optimalizaci spravovaného kódu na základě profilu)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)  
 Umožňuje ladit sestavení nativních bitových kopií pomocí běžných uživatelských scénářů. Mpgo.exe umožňuje generovat a zpracovávat profilovací data pro sestavení aplikací nativních bitových kopií (ne sestavení .NET Framework) použitím tréninkových scénářů vybraných vývojářem aplikace.  
  
 [Ngen.exe (generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 Zlepšuje výkon spravovaných aplikací použitím nativních bitových kopií (soubory obsahující zkompilovaný strojový kód závislý na procesoru). Modul runtime může ke kompilaci původního sestavení použít nativní bitové kopie z mezipaměti namísto kompilátoru JIT (just-in-time).  
  
 [Peverify.exe (nástroj PEVerify)](../../../docs/framework/tools/peverify-exe-peverify-tool.md)  
 Pomáhá ověřit, zda kód MSIL (Microsoft Intermediate Language) a přidružená metadata splňují požadavky na bezpečnost typu. Pomáhá ověřit, zda kód MSIL (Microsoft Intermediate Language) a přidružená metadata splňují požadavky na bezpečnost typu.  
  
 [Regasm.exe (nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 Načte metadata v rámci sestavení a přidá nezbytné položky do registru. To umožňuje klientům modelu COM vypadat jako třídy rozhraní .NET Framework.  
  
 [Regsvcs.exe (nástroj pro instalaci služeb .NET)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md)  
 Načte a zaregistruje sestavení, vygeneruje a nainstaluje knihovny typů do zadané aplikace modelu COM+ verze 1.0 a konfiguruje služby, které jste programově přidali do třídy.  
  
 [Resgen.exe (generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Převádí textové soubory (.txt nebo .restext) a soubory ve formátu prostředků založeném na jazyce XML (.resx) na binární soubory modulu CLR (.resources), které mohou být vloženy do binárního spustitelného souboru modulu nebo zkompilovány do satelitních sestavení.  
  
 [SecAnnotate.exe (nástroj Security Annotator rozhraní .NET)](../../../docs/framework/tools/secannotate-exe-net-security-annotator-tool.md)  
 Identifikuje části SecurityCritical a SecuritySafeCritical sestavení. Identifikuje `SecurityCritical` a `SecuritySafeCritical` části sestavení.  
  
 [SignTool.exe (nástroj pro podpis)](../../../docs/framework/tools/signtool-exe.md)  
 Digitálně podepisuje soubory, ověřuje podpisy v souborech a opatřuje soubory časovými razítky.  
  
 [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 Pomáhá vytvořit sestavení se silnými názvy. Tento nástroj poskytuje možnosti pro správu klíčů, generování podpisů a ověřování podpisů.  
  
 [SOS.dll (rozšíření ladění SOS)](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)  
 Pomáhá při ladění spravovaných programů v ladicím programu WinDbg.exe a v sadě Visual Studio poskytováním informací o vnitřním prostředí modulu CLR (Common Language Runtime).  
  
 [SqlMetal.exe (nástroj pro vytváření kódu)](../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 Generuje kód a mapování pro technologii LINQ to SQL, která je součástí rozhraní .NET Framework.  
  
 [Storeadm.exe (nástroj izolovaného úložiště)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)  
 Spravuje izolované úložiště a poskytuje možnosti pro výpis uživatelských úložišť a jejich smazání.  
  
 [Tlbexp.exe (exportér knihovny typů)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 Generuje knihovnu typů, které popisují typy definované v sestavení modulu Common Language Runtime.  
  
 [Tlbimp.exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 Převede definice typu nalezené v knihovně typů modelu COM na ekvivalentní definice v sestavení Common Language Runtime.  
  
 [Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)](../../../docs/framework/tools/winmdexp-exe-windows-runtime-metadata-export-tool.md)  
 Exportuje sestavení rozhraní .NET Framework, který se zkompiluje jako soubor .winmdobj do komponenty prostředí Windows Runtime, který je zabalené jako .winmd soubor, který obsahuje jak informace metadat a implementace prostředí Windows Runtime.  
  
 [Winres.exe (editor prostředků Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Pomáhá lokalizovat prostředky (soubory .resx nebo .resources) uživatelského rozhraní (UI), které jsou používány modelem Windows Forms. Je možné přeložit řetězce a změnit velikost, přesunout a skrýt ovládací prvky pro přizpůsobení lokalizovaných řetězců.  
  
## <a name="related-sections"></a>Související oddíly  
 [Nástroje](http://msdn.microsoft.com/library/f533241c-317c-445e-88ca-c80c8d078fca)  
 Obsahuje nástroje, jako je nástroj pro kontrolu shody (isXPS.exe) a nástroje pro profilaci výkonu.  
  
 [Nástroje Windows Communication Foundation](../../../docs/framework/wcf/tools.md)  
 Obsahuje nástroje, které usnadňují vytváření, zavádění a správu aplikací služby Windows Communication Foundation (WCF).
