---
title: 'Postupy: Instalace sestavení do globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c3bd568cf504125bc99801815d08764417b42cd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468995"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Postupy: Instalace sestavení do globální mezipaměti sestavení
Existují dva způsoby instalace sestavení se silným názvem do globální mezipaměti sestavení (GAC):  
  
> [!IMPORTANT]
>  Do mezipaměti GAC lze instalovat pouze sestavení se silným názvem. Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [postupy: podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Pomocí [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal).  
  
     V sadě Visual Studio 2012 a Visual Studio 2013 můžete tuto akci provést instalací projektu InstallShield Limited Edition.  
  
     Toto je doporučený a nejběžnější způsob přidávání sestavení do globální mezipaměti sestavení. Instalační program poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody.  
  
-   Použití [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Nástroj Gacutil.exe slouží k přidávání sestavení se silným názvem do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.  
  
    > [!NOTE]
    >  Nástroj Gacutil.exe slouží pouze pro účely vývoje a neměl by být používán k instalaci produkčních sestavení do globální mezipaměti sestavení.  
  
> [!NOTE]
>  V dřívějších verzích rozhraní .NET Framework rozšíření prostředí Shfusion.dll Windows povolit instalaci sestavení přetažením v Průzkumníku souborů. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je rozšíření Shfusion.dll zastaralé.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Používání nástroje Global Assembly Cache (Gacutil.exe)  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     **Gacutil -i** \< *název sestavení*>  
  
     V tomto příkazu *název sestavení* je název sestavení, můžete nainstalovat v globální mezipaměti sestavení.  
  
 Následující příklad nainstaluje sestavení s názvem souboru `hello.dll` do globální mezipaměti sestavení.  
  
```  
gacutil -i hello.dll  
```  
  
 Další informace najdete v tématu [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Používání projektu InstallShield Limited Edition  
  
1.  Přidat balíček instalace a nasazení do vašeho řešení tak, že otevřete místní nabídku pro vaše řešení a následným výběrem možnosti **přidat**, **nový projekt**.  
  
2.  V **přidat nový projekt** v dialogu **nainstalováno** složky, zvolte **ostatní typy projektů**, **instalace a nasazení**, **InstallShield Limited Edition**a pojmenujte svůj projekt. (Pokud se zobrazí výzva, stažení, instalaci a aktivaci programu InstallShield.)  
  
3.  Obecná konfigurace projektu instalace a nasazení provést buď pomocí Pomocník projektu v **Průzkumníka řešení**, nebo zadáním dílčích kroků jednotlivých očíslovaných kroků v **Průzkumníka řešení**. Konfigurace nastavení, jako byste nebyly přidávání sestavení do mezipaměti GAC.  
  
4.  Chcete-li zahájit proces přidávání sestavení do mezipaměti GAC, zvolte **soubory**, která se nachází v **zadat Data aplikace** vstoupit **Průzkumníka řešení**.  
  
5.  V podokně  **Složky cílového počítače** otevřete místní nabídku pro položku  **Cílový počítač** a vyberte možnost **Zobrazit předdefinovanou složku** a mezipaměť **[GlobalAssemblyCache]**.  
  
6.  V případě jednotlivých projektů v rámci řešení obsahující sestavení, které chcete nainstalovat do globální mezipaměti sestavení:  
  
    1.  V **zdrojové složky počítače** podokně, vyberte projekt.  
  
    2.  V **složky cílového počítače** podokně zvolte **[GlobalAssemblyCache]**.  
  
    3.  V **zdrojové soubory počítače** podokně zvolte **primární výstup z** *< project_name >*.  
  
    4.  Přetáhněte soubor v kroku c do **soubory cílového počítače** podokna (nebo použijte **kopírování** a **vložit** příkazy z místní nabídky souboru).  
  
## <a name="see-also"></a>Viz také  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Postupy: Odebrání sestavení z globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Nasazení Instalační služby systému Windows](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
