---
title: Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: 6261a883e7b99b7fd38da2a17ab4820c81552506
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716433"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
Instalační program .NET Framework 4,5 používá [správce restartování](/windows/win32/rstmgr/about-restart-manager) k tomu, aby se zabránilo restartování systému, kdykoli je to možné během instalace. Pokud instalační program aplikace nainstaluje .NET Framework, může pro tuto funkci využít správce restartování rozhraní. Další informace najdete v tématu [Postupy: získání průběhu z instalačního programu .NET Framework 4,5](how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Důvody pro restartování  
 Instalace .NET Framework 4,5 vyžaduje restart systému, pokud se během instalace používá aplikace .NET Framework 4. Důvodem je to, že .NET Framework 4,5 nahrazuje soubory .NET Framework 4 a vyžaduje, aby tyto soubory byly k dispozici během instalace. V mnoha případech může být restartování znemožněno neclosing.NETmi aplikacemi rozhraní Framework 4, které se používají. Některé systémové aplikace by ale neměly být zavřeny. V těchto případech se nelze vyhnout restartování.  
  
## <a name="end-user-experience"></a>Činnost koncového uživatele  
 Koncovému uživateli, který provádí úplnou instalaci .NET Framework 4,5, je dána možnost vyhnout se restartování systému, pokud instalační program zjistí .NET Framework 4 používané aplikace. Zpráva obsahuje seznam všech spuštěných aplikací .NET Framework 4 a poskytuje možnost Zavřít tyto aplikace před instalací. Pokud uživatel potvrdí, tyto aplikace se ukončí instalačním programem a zabrání se restartování systému. Pokud uživatel na zprávu během určité doby neodpoví, bude instalace pokračovat bez nutnosti zavřít žádné aplikace.  
  
 Pokud správce restartování zjistí situaci, která bude vyžadovat restartování systému i v případě, že se spuštěné aplikace zavřou, zpráva se nezobrazí.  
  
 ![Dialog Zavřít aplikaci se seznamem aktuálně spuštěných programů.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Použití zřetězeného instalačního programu  
 Pokud chcete .NET Framework znovu distribuovat s vaší aplikací, ale chcete použít vlastní instalační program a uživatelské rozhraní, můžete do procesu instalace zahrnout (zřetězit) proces instalace .NET Framework (zřetězení). Další informace o zřetězených instalacích najdete v tématu [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md). Aby se snížil restart systému v zřetězených instalacích, instalační program .NET Framework dodá instalačnímu programu seznam aplikací, které se mají zavřít. Instalační program musí tyto informace poskytnout uživateli prostřednictvím uživatelského rozhraní, jako je například okno se zprávou, získat odpověď uživatele a předat odpověď zpět instalačnímu programu .NET Framework. Příklad zřetězeného instalačního programu naleznete v článku [Postupy: získání průběhu z instalačního programu .NET Framework 4,5](how-to-get-progress-from-the-dotnet-installer.md).  
  
 Pokud používáte zřetězený instalační program, ale nechcete pro zavření aplikací zadat vlastní okno se zprávou, můžete při zřetězení procesu instalace .NET Framework použít možnosti `/showrmui` a `/passive` na příkazovém řádku. Když tyto možnosti použijete společně, instalační program zobrazí okno se zprávou pro zavření aplikací, pokud je jde zavřít, aby se zabránilo restartování systému. Toto okno se zprávou se chová stejně jako v pasivním režimu, protože je pod úplným uživatelským rozhraním. Kompletní sadu možností příkazového řádku pro .NET Framework redistributable najdete v [Průvodci nasazením pro vývojáře](deployment-guide-for-developers.md) .  
  
## <a name="see-also"></a>Viz také:

- [Nasazení](index.md)
- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
