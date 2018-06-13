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
ms.openlocfilehash: e54dcb585c06f2bf49c41f763e03e5624a033442
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388905"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Používá instalační program [restartovat správce](http://go.microsoft.com/fwlink/?LinkId=231425) aby systému restartuje kdykoli je to možné během instalace. Pokud vaše aplikace Instalační program nainstaluje rozhraní .NET Framework, můžete rozhraní pomocí Správce restartování využít této funkce. Další informace najdete v tématu [postupy: získání průběh z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Důvody pro restartování  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Instalace vyžaduje restartování systému, pokud aplikace rozhraní .NET Framework 4 se používá během instalace. Důvodem je, že [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nahradí soubory rozhraní .NET Framework 4 a vyžaduje, aby se během instalace k dispozici tyto soubory. V mnoha případech je možné zabránit restartování podle ho preventivně detekovat a closing.NET Framework 4 aplikace, které jsou používány. Ale některé aplikace systému by neměl být ukončeny. V těchto případech nelze vyhnout spojení restartování.  
  
## <a name="end-user-experience"></a>Činnost koncového uživatele  
 S koncovým uživatelem, který provádí úplnou instalaci systému [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] je zadána možnost vyhnout restartování systému, pokud instalační program zjistí aplikace rozhraní .NET Framework 4 používán. Zpráva uvádí všechny spuštěné aplikace rozhraní .NET Framework 4 a nabízí možnost Zavřít tyto aplikace před instalací. Pokud uživatel potvrdí, tyto aplikace jsou vypnuty instalační program a je vyhnout restartování systému. Pokud uživatel neodpovídá na zprávy v rámci množství času, instalace bude pokračovat bez zavření všech aplikací.  
  
 Pokud správce restartování zjistí situaci, který bude vyžadovat restartování systému, i v případě spouštění aplikací jsou uzavřeny, zpráva se nezobrazí.  
  
 ![Zavřete dialogové okno aplikace](../../../docs/framework/deployment/media/closeapplicationdialog.png "CloseApplicationDialog")  
Výzva k zadání zavírání aplikací rozhraní .NET Framework, které jsou používány  
  
## <a name="using-a-chained-installer"></a>Pomocí zřetězené instalačního programu  
 Pokud chcete znovu distribuovat rozhraní .NET Framework s vaší aplikací, ale chcete použít vlastní instalační program a uživatelského rozhraní, můžete zahrnout procesu instalace (řetězec) rozhraní .NET Framework pro váš proces instalace. Další informace o zřetězené instalace najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md). Aby se snížilo restartování systému v zřetězené instalace, instalační program rozhraní .NET Framework poskytuje vaše instalační program se seznamem ukončení aplikací. Instalační program musí poskytnout tyto informace pro uživatele pomocí uživatelského rozhraní, jako je například okno se zprávou, získat odpovědi uživatele a pak předejte odpověď zpět do instalační program rozhraní .NET Framework. Příklad zřetězené instalační program, najdete v článku [postupy: získání průběh z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Pokud používáte zřetězené instalační program, ale nechcete zadat vlastní okno se zprávou pro zavření aplikace, můžete použít `/showrmui` a `/passive` instalace možností příkazového řádku při zřetězení rozhraní .NET Framework. Použijete-li tyto možnosti společně, instalační program zobrazí pole zpráv pro zavření aplikace, pokud je možné uzavřít předejdete restartování systému. Toto okno se zprávou se chová stejně v pasivním režimu stejně jako v rámci úplné uživatelské rozhraní. V tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md) pro kompletní sadu možností příkazového řádku pro rozhraní .NET Framework redistributable.  
  
## <a name="see-also"></a>Viz také  
 [Nasazení](../../../docs/framework/deployment/index.md)  
 [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
