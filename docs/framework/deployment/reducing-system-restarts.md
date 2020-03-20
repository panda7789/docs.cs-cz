---
title: Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: 6261a883e7b99b7fd38da2a17ab4820c81552506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716433"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
Instalační program rozhraní .NET Framework 4.5 používá [Správce restartování,](/windows/win32/rstmgr/about-restart-manager) aby zabránil restartování systému, kdykoli je to možné během instalace. Pokud instalační program aplikace nainstaluje rozhraní .NET Framework, může rozhraní s Správce restartu využít této funkce. Další informace naleznete v [tématu How to: Get Progress from the .NET Framework 4.5 Installer](how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Důvody pro restartování  
 Instalace rozhraní .NET Framework 4.5 vyžaduje restartování systému, pokud je během instalace používána aplikace .NET Framework 4. Důvodem je, že rozhraní .NET Framework 4.5 nahrazuje soubory rozhraní .NET Framework 4 a vyžaduje, aby tyto soubory byly během instalace k dispozici. V mnoha případech lze zabránit restartování preventivní detekcí a closing.NET aplikace framework u 4, které jsou používány. Některé systémové aplikace by však neměly být uzavřeny. V těchto případech nelze zabránit restartování.  
  
## <a name="end-user-experience"></a>Prostředí pro koncové uživatele  
 Koncový uživatel, který provádí úplnou instalaci rozhraní .NET Framework 4.5, má možnost vyhnout se restartování systému, pokud instalační program zjistí, že se používají aplikace rozhraní .NET Framework 4. Zpráva obsahuje seznam všech spuštěné aplikace rozhraní .NET Framework 4 a poskytuje možnost ukončit tyto aplikace před instalací. Pokud uživatel potvrdí, tyto aplikace jsou vypnuty instalačním programem a je zabráněno restartování systému. Pokud uživatel neodpoví na zprávu v určitém časovém období, instalace pokračuje bez zavření všech aplikací.  
  
 Pokud Správce restartování zjistí situaci, která bude vyžadovat restartování systému i v případě, že jsou spuštěné aplikace zavřené, zpráva se nezobrazí.  
  
 ![Dialogové okno Zavřít aplikaci se seznamem aktuálně spuštěných programů.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Použití zřetězeného instalačního programu  
 Pokud chcete redistribuovat rozhraní .NET Framework s vaší aplikací, ale chcete použít vlastní instalační program a ui, můžete zahrnout (řetězový) proces nastavení rozhraní .NET Framework do procesu instalace. Další informace o zřetězených instalacích naleznete v [Příručce pro nasazení pro vývojáře](deployment-guide-for-developers.md). Chcete-li snížit restartování systému v řetězových instalacích, instalační program rozhraní .NET Framework poskytuje instalační program se seznamem aplikací, které chcete zavřít. Instalační program musí poskytnout tyto informace uživateli prostřednictvím uživatelského rozhraní, jako je například okno se zprávou, získat odpověď uživatele a potom předat odpověď zpět instalačnímu programu rozhraní .NET Framework. Příklad zřetězeného instalačního programu naleznete v článku [How to: Get Progress from the .NET Framework 4.5 Installer](how-to-get-progress-from-the-dotnet-installer.md).  
  
 Pokud používáte zřetězený instalační program, ale nechcete poskytnout vlastní okno se zprávou `/showrmui` `/passive` pro zavírání aplikací, můžete při řetězovém řetězci procesu instalace rozhraní .NET Framework použít možnosti a na příkazovém řádku. Při použití těchto možností společně, instalační program zobrazí okno se zprávou pro zavření aplikací, pokud mohou být uzavřeny, aby se zabránilo restartování systému. Toto okno se zprávou se chová stejně v pasivním režimu jako v rámci úplného uživatelského rozhraní. Kompletní sadu možností příkazového řádku pro redistribuovatelné rozhraní .NET Framework naleznete [v průvodci nasazením pro vývojáře.](deployment-guide-for-developers.md)  
  
## <a name="see-also"></a>Viz také

- [Nasazení](index.md)
- [Průvodce nasazením pro vývojáře](deployment-guide-for-developers.md)
- [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
