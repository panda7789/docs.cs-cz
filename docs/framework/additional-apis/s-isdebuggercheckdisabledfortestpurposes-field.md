---
title: s_isDebuggerCheckDisabledForTestPurposes pole
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name: System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location: PresentationCore.dll
api_type: Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.workload: dotnet
ms.openlocfilehash: 67da38d958d153ebe526f298785b39afb7be6513
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes pole

Toto pole privátní v `System.Windows.Diagnostics.VisualDiagnostics` třída se používá Visual Studio k určení, zda se provede interní kontrola pro aktivní ladicí program.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  Rozhraní API v `System.Windows.Diagnostics.VisualDiagnostics` třídy jsou dostupné, jenom když aplikace běží pod ladicí program. Nastavit `s_isDebuggerCheckDisabledForTestPurposes` k `true` pro přístup k rozhraní API mimo ladicí program.  
>   
>  Společnost Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.  

## <a name="requirements"></a>Požadavky

**Namespace:**<xref:System.Windows.Diagnostics>

**Sestavení:** PresentationCore (v knihovně PresentationCore.dll)

**Verze rozhraní .NET framework:** dostupné od verze 4.6.
