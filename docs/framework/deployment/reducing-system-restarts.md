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
ms.openlocfilehash: a491b0efd38ed7ff37c8c704b6646dddede5efb3
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379922"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Omezení restartů systému při instalaci rozhraní .NET Framework 4.5
Použije instalační program rozhraní .NET Framework 4.5 [správce restartování](https://go.microsoft.com/fwlink/?LinkId=231425) zabraňuje systému v restartování během instalace. Pokud vaše aplikace Instalační program nainstaluje rozhraní .NET Framework, můžete rozhraní s správce restartování, abyste mohli využít tuto funkci. Další informace najdete v tématu [jak: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
## <a name="reasons-for-a-restart"></a>Důvody pro restartování  
 Instalace rozhraní .NET Framework 4.5 vyžaduje restartování systému, pokud aplikace rozhraní .NET Framework 4 se používá během instalace. Je to proto, že rozhraní .NET Framework 4.5 nahradí soubory rozhraní .NET Framework 4 a vyžaduje, aby se během instalace k dispozici tyto soubory. V mnoha případech lze zabránit restartování preventivně zjišťování a closing.NET Framework 4 aplikace, které se používají. Však některé aplikace pro systém by neměl být uzavřena. V těchto případech se nelze vyhnout spojení restartování.  
  
## <a name="end-user-experience"></a>Činnost koncového uživatele  
 Koncový uživatel, který provádí úplnou instalaci rozhraní .NET Framework 4.5 je umožněno instalační program zjistí aplikace rozhraní .NET Framework 4, používá-li zabránit restartování systému. Zpráva obsahuje seznam všech spuštěných aplikací rozhraní .NET Framework 4 a poskytuje možnost Zavřít tyto aplikace před instalací. Pokud uživatel potvrdí, tyto aplikace se vypne instalační službou a zabránit restartování systému. Pokud uživatel neodpovídá na zprávu v rámci určité množství času, instalace bude pokračovat bez zavření všech aplikací.  
  
 Pokud správce restartování zjistí situaci, která bude vyžadovat restart systému, i v případě používání aplikací zavřete, zpráva se nezobrazí.  
  
 ![Dialogové okno zavřít aplikaci výpis aktuálně spuštěné.](./media/reducing-system-restarts/close-application-dialog.png)  
  
## <a name="using-a-chained-installer"></a>Pomocí zřetězené instalačního programu  
 Pokud chcete dále distribuovat rozhraní .NET Framework s vaší aplikací, ale chcete použít vlastní instalační program a uživatelského rozhraní, můžete zahrnout instalaci (řetězec) rozhraní .NET Framework pro váš proces instalace. Další informace o zřetězené instalace najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md). Ke snížení restartování systému v zřetězené instalace Instalační služby rozhraní .NET Framework poskytuje vašem instalačním programu se seznamem aplikací zavřete. Instalační program musí poskytnout tyto informace pro uživatele prostřednictvím uživatelského rozhraní, jako je okno se zprávou, získání odpovědi uživatele a pak předejte odpověď zpět do instalačního programu .NET Framework. Příklad zřetězené instalačního programu, najdete v článku [jak: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md).  
  
 Pokud používáte zřetězené instalační program, ale nechcete zadat vlastní okno se zprávou pro uzavření aplikace, můžete použít `/showrmui` a `/passive` nastavení možnosti příkazového řádku při řetězení rozhraní .NET Framework. Použijete-li tyto možnosti společně, instalační program ukazuje okně se zprávou pro uzavření aplikace, pokud jej lze zavřít, aby restartování systému. Toto okno se zprávou se chová stejně v pasivním režimu stejně jako v části úplné uživatelské rozhraní. Zobrazit [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md) pro kompletní sadu možností příkazového řádku pro rozhraní .NET Framework, distribuovatelné součásti.  
  
## <a name="see-also"></a>Viz také:

- [Nasazení](../../../docs/framework/deployment/index.md)
- [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [Postupy: Získání procesu z instalačního programu .NET Framework 4.5](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)
