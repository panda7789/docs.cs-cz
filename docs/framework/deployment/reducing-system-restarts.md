---
title: Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b24cc4b0ad2839d2c2fa099f963b13a5532d39df
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452885"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Použije instalační program [správce restartování](https://go.microsoft.com/fwlink/?LinkId=231425) zabraňuje systému v restartování během instalace. Pokud vaše aplikace Instalační program nainstaluje rozhraní .NET Framework, můžete rozhraní s správce restartování, abyste mohli využít tuto funkci. Další informace najdete v tématu [postupy: získání průběhu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Důvody pro restartování  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalace vyžaduje restartování systému, pokud aplikace rozhraní .NET Framework 4 se používá během instalace. Je to proto, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nahradí soubory rozhraní .NET Framework 4 a vyžaduje, aby se během instalace k dispozici tyto soubory. V mnoha případech lze zabránit restartování preventivně zjišťování a closing.NET Framework 4 aplikace, které se používají. Však některé aplikace pro systém by neměl být uzavřena. V těchto případech se nelze vyhnout spojení restartování.  
  
## <a name="end-user-experience"></a>Činnost koncového uživatele  
 Koncový uživatel, kdo dělá úplnou instalaci nástroje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] je zadána možnost vyhnout se restartování systému, pokud instalační program zjistí aplikace rozhraní .NET Framework 4, používá. Zpráva obsahuje seznam všech spuštěných aplikací rozhraní .NET Framework 4 a poskytuje možnost Zavřít tyto aplikace před instalací. Pokud uživatel potvrdí, tyto aplikace se vypne instalační službou a zabránit restartování systému. Pokud uživatel neodpovídá na zprávu v rámci určité množství času, instalace bude pokračovat bez zavření všech aplikací.  
  
 Pokud správce restartování zjistí situaci, která bude vyžadovat restart systému, i v případě používání aplikací zavřete, zpráva se nezobrazí.  
  
 ![Zavřete dialogové okno aplikace](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
Zavření aplikací rozhraní .NET Framework, které se používají k zadání  
  
## <a name="using-a-chained-installer"></a>Pomocí zřetězené instalačního programu  
 Pokud chcete dále distribuovat rozhraní .NET Framework s vaší aplikací, ale chcete použít vlastní instalační program a uživatelského rozhraní, můžete zahrnout instalaci (řetězec) rozhraní .NET Framework pro váš proces instalace. Další informace o zřetězené instalace najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md). Ke snížení restartování systému v zřetězené instalace Instalační služby rozhraní .NET Framework poskytuje vašem instalačním programu se seznamem aplikací zavřete. Instalační program musí poskytnout tyto informace pro uživatele prostřednictvím uživatelského rozhraní, jako je okno se zprávou, získání odpovědi uživatele a pak předejte odpověď zpět do instalačního programu .NET Framework. Příklad zřetězené instalačního programu, najdete v článku [postupy: získání průběhu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Pokud používáte zřetězené instalační program, ale nechcete zadat vlastní okno se zprávou pro uzavření aplikace, můžete použít `/showrmui` a `/passive` nastavení možnosti příkazového řádku při řetězení rozhraní .NET Framework. Použijete-li tyto možnosti společně, instalační program ukazuje okně se zprávou pro uzavření aplikace, pokud jej lze zavřít, aby restartování systému. Toto okno se zprávou se chová stejně v pasivním režimu stejně jako v části úplné uživatelské rozhraní. Zobrazit [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md) pro kompletní sadu možností příkazového řádku pro rozhraní .NET Framework, distribuovatelné součásti.  
  
## <a name="see-also"></a>Viz také  
- [Nasazení](../../../docs/framework/deployment/index.md)  
- [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
- [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
