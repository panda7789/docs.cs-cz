---
title: "Stažení balíčku obslužné rutiny webových tokenů JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d3821ff1da945df7c6e07e5baf69730173eacc87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a>Stažení balíčku obslužné rutiny webových tokenů JSON
Toto téma popisuje, jak stáhnout a použít JSON obslužná rutina webových tokenů ve vašem projektu.  
  
## <a name="downloading-the-json-web-token-handler"></a>Stažení obslužné rutiny webových tokenů JSON  
 Obslužná rutina webových tokenů JSON rozšíření není k dispozici jako balíčku NuGet, který přidá nezbytné sestavení a odkazy na projekt. Pokud již nemáte NuGet nainstalovaná, přejděte na [nuget.org](http://nuget.org) k její instalaci. Zobrazí historii Správa verzí pro rozšíření navštivte stránku s jeho na NuGet: [JSON obslužná rutina webových tokenů na NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a>Stahování obslužná rutina tokenu JSON Web pomocí grafického uživatelského rozhraní Správce balíčků  
  
1.  V sadě Visual Studio, klikněte pravým tlačítkem na projekt v **Průzkumníku řešení**a potom vyberte **spravovat balíčky NuGet**.  
  
2.  V **spravovat balíčky NuGet** okně klikněte na vyhledávací pole a zadejte `JWT Token Handler` a stiskněte klávesu **Enter**.  
  
3.  V podokně výsledků klikněte na **nainstalovat** tlačítko pro první výsledek.  
  
4.  Balíček zahájíte stahování. Před přidáním do projektu, zobrazí se dialogové okno přijetí licence. Pokud souhlasíte s licenčními podmínkami, klikněte na tlačítko **souhlasím**.  
  
5.  Nejnovější sestavení obslužná rutina webových tokenů JSON, bude možné stáhnout a přidat do projektu.  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a>Stahování obslužná rutina tokenu JSON Web pomocí konzoly Správce balíčků  
  
1.  V sadě Visual Studio, klikněte na tlačítko **nástroje**, **Správce balíčků knihoven**a potom **Konzola správce balíčků**.  
  
2.  **Konzola správce balíčků** se zobrazí. Zadejte následující text a stiskněte klávesu **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  Nejnovější sestavení obslužná rutina webových tokenů JSON, bude možné stáhnout a přidat do projektu.
