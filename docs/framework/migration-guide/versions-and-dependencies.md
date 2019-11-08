---
title: Verze a závislosti rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: eadb456bafb1703c687e73c6aecc81c9dccae72c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739564"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework verze a závislosti

Všechny verze rozhraní .NET Framework obsahují modul Common Language Runtime (CLR), knihovny základních tříd a další spravované knihovny. Toto téma popisuje klíčové funkce rozhraní .NET Framework podle verzí, poskytuje informace o základních verzích CLR a přidružených vývojových prostředích a identifikuje verze, které jsou nainstalovány v operačním systému Windows.  
  
> [!NOTE]
> Informace o stažení a instalaci .NET Framework najdete v tématu [instalace .NET Framework pro vývojáře](../install/guide-for-developers.md).  
  
Následující tabulka shrnuje .NET Framework historii verzí a koreluje každou verzi se sadou Visual Studio, Windows a Windows serverem. Visual Studio poskytuje cílení na více verzí, takže nejste omezeni na verzi .NET Framework, která je uvedena v seznamu.  
  
Každá nová verze rozhraní .NET Framework zachovává funkce předchozích verzí a přidává nové funkce. Modul CLR je identifikován vlastním číslem verze. Číslo verze rozhraní .NET Framework je při každém vydání zvýšeno, i když není vždy zvýšena verze modulu CLR. Například .NET Framework 4, 4,5 a novější verze zahrnují modul CLR 4, ale .NET Framework 2,0, 3,0 a 3,5 zahrnují 2,0 CLR. (Verze 3 CLR neexistovala.)  
  
Úplný seznam podporovaných operačních systémů najdete v části [požadavky na systém](../get-started/system-requirements.md) . Informace ke stažení najdete v tématu [instalace .NET Framework pro vývojáře](../install/guide-for-developers.md). Informace o určení, které verze .NET Framework jsou nainstalovány v počítači, naleznete v tématu [How to: určující, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).  
  
V tabulce jsou verze .NET Framework nainstalované na verzích operačního systému označené ✓em v části **zahrnuté v/můžou být nainstalované v systému Windows** a **zahrnuté v/může být nainstalované ve sloupcích Windows serveru** musí být [povolené v ovládacím prvku. Panel](../install/dotnet-35-windows-10.md) (pro systém Windows) nebo povolený prostřednictvím Správce serveru (pro Windows Server).  

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]
 
|Verze rozhraní .NET Framework|Verze CLR|Zahrnuto v<br /> Visual Studio<br/>verze|✓ Zahrnutý v<br />+ Může být nainstalováno na<br />Windows|✓ Zahrnutý v<br />+ Může být nainstalováno na<br />Windows Server|Určení nainstalované verze rozhraní .NET|  
|----------------------------|-----------------|--------------|---------------------------------------|----------------------------------------------------|-----------------------------------------------------------|-----------------------------------------| 
|4,8<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-48)<br/><br/>[Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)|4| | ✓ 10 května 2019 Update<br/><br/> + 10. října 2018 Update (verze 1809) <br/> + 10. dubna 2018 Update (verze 1803) <br/> + 10 poklesnoutch Creators Update (verze 1709) <br/> + 10 Creators Update (verze 1703) <br/> + 10 aktualizace pro výročí (verze 1607) <br/> + 8,1 <br/> \+ 7 | + Windows Server 2019<br/> + Windows Server, verze 1809 <br/> + Windows Server, verze 1803 <br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Použít `Release` DWORD:<br/><br/> -528040 (aktualizace z Windows 10 se dá 2019) <br/> -528049 (všechny ostatní verze operačního systému) <br/><br/> (viz [pokyny](how-to-determine-which-versions-are-installed.md))|
|4.7.2<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-472)<br/><br/>[Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)|4| | ✓ 10. října 2018 Update (verze 1809) <br/> ✓ 10. dubna 2018 Update (verze 1803) <br/><br/> + 10 poklesnoutch Creators Update (verze 1709) <br/> + 10 Creators Update (verze 1703) <br/> + 10 aktualizace pro výročí (verze 1607) <br/> + 8,1 <br/> \+ 7 | ✓ Windows Server 2019<br/> ✓ Windows Server verze 1809 <br/> ✓ Windows Server verze 1803 <br/><br/> + Windows Server, verze 1709 <br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Použít `Release` DWORD:<br/><br/> -461814 (aktualizace Windows 10 říjen 2018) <br/> -461808 (aktualizace Windows 10 z dubna 2018 a Windows Server, verze 1803) <br/> -461814 (všechny ostatní verze operačního systému) <br/><br/> (viz [pokyny](how-to-determine-which-versions-are-installed.md))|
|4.7.1<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-471)<br/><br/>[Novinka v přístupnosti](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)|4| | ✓ 10 – Creators Update (verze 1709) <br/> <br/> + 10 Creators Update (verze 1703) <br/> + 10 aktualizace pro výročí (verze 1607) <br/> + 8,1 <br/> \+ 7| + Windows Server, verze 1803 <br/><br/> ✓ Windows Server verze 1709 <br/><br/> + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Použít `Release` DWORD:<br/><br/> -461308 (Windows 10 Creators Update a Windows Server, verze 1709) <br/> -461310 (všechny ostatní verze operačního systému) <br/><br/> (viz [pokyny](how-to-determine-which-versions-are-installed.md))| 
|4,7<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-47)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)|4| | ✓ 10 Creators Update (verze 1703) <br/> <br/> + 10 aktualizace pro výročí (verze 1607) <br/> + 8,1 <br/> \+ 7| + 2016 <br/> + 2012 R2 <br/> + 2012 <br/> + 2008 R2 SP1 |Použít `Release` DWORD:<br/><br/> -460798 (Windows 10 Creators Update) <br/> -460805 (všechny ostatní verze operačního systému) <br/><br/> (viz [pokyny](how-to-determine-which-versions-are-installed.md)) |  
|4.6.2<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-462)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)|4||✓ 10 – aktualizace pro výročí (verze 1607) <br /><br /> + 10 listopadu Update (verze 1511) <br/> + 10 <br/> + 8,1<br />+ 7|✓ 2016<br /><br /> + 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|Použít `Release` DWORD:<br /><br /> -394802 (aktualizace pro Windows 10 – výročí a Windows Server 2016) <br />-394806 (všechny ostatní verze operačního systému)<br /><br /> (viz [pokyny](how-to-determine-which-versions-are-installed.md))|  
|4.6.1<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-461)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)|4||✓ 10 listopadu Update (verze 1511) <br /><br /> + 10<br />+ 8,1<br />+ 8<br />+ 7|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1|Použít `Release` DWORD:<br /><br /> -394254 (aktualizace Windows 10 listopadu)<br />-394271 (všechny ostatní verze operačního systému)<br /><br /> (viz [pokyny](how-to-determine-which-versions-are-installed.md))|  
|4.6<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-2015)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)|4|2015|✓ 10<br /><br />+ 8,1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Použít `Release` DWORD:<br /><br /> -393295 (Windows 10)<br />-393297 (všechny ostatní verze operačního systému)<br /><br /> (viz [pokyny](how-to-determine-which-versions-are-installed.md))|  
|4.5.2<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-452)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)|4|-|+ 8,1<br />+ 8<br />+ 7<br />+ Vista|+ 2012 R2<br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Použít `Release` DWORD:<br /><br /> 379893<br /><br />(viz [pokyny](how-to-determine-which-versions-are-installed.md))|  
|4.5.1<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-451)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)|4|2013|✓ 8,1<br /><br />+ 8<br />+ 7<br />+ Vista|✓ 2012 R2<br /><br />+ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Použít `Release` DWORD:<br /><br /> -378675 (Windows 8.1)<br />-378758 (vše ostatní)<br /><br /> (viz [pokyny](how-to-determine-which-versions-are-installed.md))|  
|4.5<br/><br/>[Nové funkce](../whats-new/index.md#whats-new-in-net-framework-45)<br /><br >[Zpráva k vydání verze](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)|4|2012|✓ 8<br />+ 7<br />+ Vista|✓ 2012<br />+ 2008 R2 SP1<br />+ 2008 SP2|Použít `Release` DWORD:<br /><br /> 378389<br /><br />(viz [pokyny](how-to-determine-which-versions-are-installed.md))|  
|4<br/><br/>[Nové funkce](../whats-new/index.md)|4|2010|+ 7<br />+ Vista|+ 2008 R2 SP1<br />+ 2008 SP2<br />+ 2003|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|  
|3.5<br/><br/>[Nové funkce](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))|2.0|2008|✓ 10\*<br/>✓ 8,1\*<br />✓ 8\*<br />✓ 7<br /><br />+ Vista|  A Windows Server verze 1803\* <br/> A Windows Server verze 1709\* <br/> + 2016\* <br/>+ 2012 R2\*<br />+ 2012\*<br /><br />✓ 2008 R2 SP1\*<br /><br/>+ 2008 SP2<br />+ 2003|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|  
|3.0<br/><br/>Nový:<br/>WPF, WCF, WF, CardSpace|2.0|-|✓ Vista|✓ 2008 R2 SP1 *<br />✓ 2008 SP2\*<br /><br />+ 2003|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|  
|2.0<br/><br/>[Nové funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/ms229284\(v%3dvs.80\))|2.0|2005|-|✓ 2008 R2 SP1<br />✓ 2008 SP2<br />✓ 2003|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|  
|1.1<br/><br/>[Nové funkce](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/9wtde3k4\(v%3dvs.71\))|1.1|2003|-|✓ 2003|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|  
|1.0|1.0|Visual Studio .NET|-|-|Zobrazit [pokyny](how-to-determine-which-versions-are-installed.md)|  

> [!NOTE]
>
> - .NET Framework musí být v tomto operačním systému povolená přes [Ovládací panely (pro Windows) nebo správce serveru (pro Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).
> - Obecně platí, že byste neměli odinstalovávat verze rozhraní .NET Framework, které jsou nainstalovány ve vašem počítači, protože na konkrétní verzi může záviset aplikace, kterou používáte, a ta se může poškodit, pokud je verze odebrána. V jednom počítači můžete najednou načíst několik verzí rozhraní .NET Framework. To znamená, že můžete nainstalovat .NET Framework bez nutnosti odinstalování předchozích verzí. Další informace najdete v tématu [Začínáme](../get-started/index.md).

## <a name="target-and-run-apps-for-version-45-and-later"></a>Cílení a spouštění aplikací pro verzi 4,5 a novější

.NET Framework 4,5 je místní aktualizace, která nahrazuje .NET Framework 4 ve vašem počítači a podobně .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 a 4,8 jsou místní aktualizace .NET Framework 4,5, což znamená, že používají stejný modul runtime. verze, ale aktualizované verze sestavení a zahrnutí nových typů a členů. Po instalaci jedné z těchto aktualizací by se .NET Framework 4, .NET Framework 4,5, .NET Framework 4,6 nebo .NET Framework 4,7, aby aplikace běžely i bez nutnosti opětovné kompilace. Opačně to však neplatí. Nedoporučujeme spouštět aplikace, které cílí na novější verzi .NET Framework ve starší verzi .NET Framework. Například nedoporučujeme spouštět aplikaci cíle .NET Framework 4,6 na .NET Framework 4,5. Platí následující pokyny:  
  
- V sadě Visual Studio můžete zvolit .NET Framework 4,5 jako cílovou architekturu projektu (tím se nastaví vlastnost <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType>) pro zkompilování projektu jako sestavení nebo spustitelný soubor .NET Framework 4,5. Toto sestavení nebo spustitelný soubor je pak možné použít na jakémkoli počítači s nainstalovanou .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8.  
  
- V aplikaci Visual Studio můžete zvolit .NET Framework 4.5.1 jako cílovou architekturu projektu, aby byla zkompilována jako sestavení .NET Framework 4.5.1 nebo spustitelný soubor. Toto sestavení nebo spustitelný soubor spouštějte pouze v počítačích, ve kterých je nainstalována .NET Framework 4.5.1 nebo novější. Spuštění spustitelného souboru, který cílí na .NET Framework 4.5.1, bude zablokováno v počítači, ve kterém je nainstalována pouze starší verze .NET Framework, například .NET Framework 4,5. Uživateli se zobrazí výzva k instalaci .NET Framework 4.5.1. Kromě toho .NET Framework 4.5.1 sestavení nesmí být voláno z aplikace, která cílí na starší verzi .NET Framework, jako je například .NET Framework 4,5.  
  
  > [!NOTE]
  > .NET Framework 4.5.1 a .NET Framework 4,5 se tady používají jenom jako příklady. Popsaná zásada se vztahuje na všechny aplikace, které cílí na novější verzi .NET Framework než ta, která je nainstalovaná v systému, ve kterém je spuštěná.  
  
Některé změny v .NET Framework mohou vyžadovat změny kódu vaší aplikace. Pokud používáte existující aplikaci v .NET Framework 4,5 nebo novějším, přečtěte si článek [Kompatibilita aplikací](application-compatibility.md). Informace o instalaci aktuální verze najdete v tématu [instalace .NET Framework pro vývojáře](../install/guide-for-developers.md). Informace o podpoře pro .NET Framework najdete v tématu [Zásady životního cyklu podpory Microsoft .NET Framework](https://support.microsoft.com/help/17455/lifecycle-faq-net-framework) na webu Podpora Microsoftu.  
  
## <a name="target-and-run-apps-for-older-versions"></a>Cílení a spouštění aplikací pro starší verze  

.NET Framework verze 2,0, 3,0 a 3,5 jsou sestavené se stejnou verzí modulu CLR (CLR 2,0). Tyto verze představují sousední vrstvy jedné instalace. Každá verze je postupně sestavena nad předchozí verzí. Na počítači není možné spouštět verze 2,0, 3,0 a 3,5 vedle sebe. Při instalaci verze 3.5 automaticky získáte vrstvy 2.0 a 3.0 a aplikace, které byly vytvořeny pro verze 2.0, 3.0 a 3.5, lze spustit na verzi 3.5. .NET Framework 4 ale tento přístup k vrstvení a novější verze (.NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 a 4,8) také reprezentují po sobě jdoucí vrstvy jedné instalace. Počínaje .NET Framework 4 můžete použít vnitroprocesové hostování vedle sebe, aby se spouštělo více verzí modulu CLR v jednom procesu. Další informace naleznete v tématu [sestavení a souběžné spouštění](../../standard/assembly/side-by-side-execution.md).  
  
Kromě toho, pokud je vaše aplikace cílena na verzi 2,0, 3,0 nebo 3,5, mohou být uživatelé požádáni o povolení .NET Framework 3,5 na počítači se systémem Windows 8, Windows 8.1 nebo Windows 10 před tím, než budou moci aplikaci spustit. Další informace najdete v tématu [instalace .NET Framework 3,5 ve Windows 10, Windows 8.1 a Windows 8](../install/dotnet-35-windows-10.md).  
  
## <a name="next-steps"></a>Další kroky  
  
- Pokud s .NET Framework začínáte, přečtěte si [Přehled](../get-started/overview.md) úvodních konceptů a funkcí.  
  
- Nové funkce a vylepšení .NET Framework 4,5 a jejich vydání najdete v tématu [co je nového v .NET Framework](../whats-new/index.md).  
  
- Informace o migraci aplikace na novější verzi .NET Framework najdete v [Průvodci migrací](index.md).
  
- Informace o určení, které verze nebo aktualizace jsou nainstalovány v počítači, naleznete v tématu [Postupy: určení, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md) a [Postupy: určení, které .NET Framework aktualizace jsou nainstalovány](how-to-determine-which-net-framework-updates-are-installed.md).  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita verzí](version-compatibility.md)
- [Zásady životního cyklu podpory pro Microsoft .NET Framework](https://support.microsoft.com/help/17455/lifecycle-faq-net-framework)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
