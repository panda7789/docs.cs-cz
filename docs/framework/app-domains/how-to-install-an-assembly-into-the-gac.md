---
title: "Postupy: Instalace sestavení do globální mezipaměti sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23a1d8c638b198c31d7c83aaf3f216b465f01453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Postupy: Instalace sestavení do globální mezipaměti sestavení
Existují dva způsoby instalace sestavení se silným názvem do globální mezipaměti sestavení (GAC):  
  
> [!IMPORTANT]
>  Do mezipaměti GAC lze instalovat pouze sestavení se silným názvem. Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [postupy: podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Pomocí [Instalační služby systému Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).  
  
     V sadě Visual Studio 2012 a Visual Studio 2013 můžete tuto akci provést instalací projektu InstallShield Limited Edition.  
  
     Toto je doporučený a nejběžnější způsob přidávání sestavení do globální mezipaměti sestavení. Instalační program poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody.  
  
-   Pomocí [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Nástroj Gacutil.exe slouží k přidávání sestavení se silným názvem do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.  
  
    > [!NOTE]
    >  Nástroj Gacutil.exe slouží pouze pro účely vývoje a neměl by být používán k instalaci produkčních sestavení do globální mezipaměti sestavení.  
  
> [!NOTE]
>  V dřívějších verzích rozhraní .NET Framework povolené rozšíření pro prostředí Shfusion.dll Windows nainstalovat sestavení tak, že je přetáhnete v Průzkumníku souborů. Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll je zastaralý.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Používání nástroje Global Assembly Cache (Gacutil.exe)  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     **Gacutil -i** \< *název sestavení*>  
  
     V tomto příkazu *název sestavení* je název sestavení pro instalaci v globální mezipaměti sestavení.  
  
 Následující příklad nainstaluje sestavení s názvem souboru `hello.dll` do globální mezipaměti sestavení.  
  
```  
gacutil -i hello.dll  
```  
  
 Další informace najdete v tématu [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Používání projektu InstallShield Limited Edition  
  
1.  Přidání balíčku instalace a nasazení do řešení otevřením místní nabídku pro vaše řešení, a pak vyberete **přidat**, **nový projekt**.  
  
2.  V **přidat nový projekt** dialogovém **nainstalovaná** složky, vyberte **jiné typy projektů**, **instalace a nasazení**, **InstallShield Limited Edition**a zadejte název projektu. (Pokud se zobrazí výzva, stáhnout, nainstalovat a aktivovat InstallShield.)  
  
3.  Provedení obecné konfigurace instalace a nasazení projektu, buď pomocí Pomocníka pro projekt v **Průzkumníku řešení**, nebo výběrem dílčích kroků číslované kroky **Průzkumníku řešení**. Konfigurace vašeho nastavení, jako při sestavení nebyly přidání do mezipaměti GAC.  
  
4.  Chcete-li zahájit proces přidávání sestavení do mezipaměti GAC, zvolte **soubory**, který je v části **zadejte Data aplikací** krok v **Průzkumníku řešení**.  
  
5.  V **složek na cílovém počítači** podokně otevřete místní nabídku pro **cílový počítač**a potom zvolte **zobrazit předdefinované složku**, **[GlobalAssemblyCache]**.  
  
6.  V případě jednotlivých projektů v rámci řešení obsahující sestavení, které chcete nainstalovat do globální mezipaměti sestavení:  
  
    1.  V **zdrojové složky počítače** podokně vyberte projekt.  
  
    2.  V **složek na cílovém počítači** podokně vyberte **[GlobalAssemblyCache]**.  
  
    3.  V **zdrojové soubory počítače** podokně vyberte **primární výstup z** *< název_projektu >*.  
  
    4.  Přetáhněte soubor v kroku c **soubory v cílovém počítači** podokně (nebo použijte **kopie** a **vložení** příkazy z místní nabídky souboru).  
  
## <a name="see-also"></a>Viz také  
 [Práce se sestaveními a globální mezipaměti sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Postupy: odebrání sestavení z globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Postupy: podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Instalační služba systému Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
