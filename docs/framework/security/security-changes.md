---
title: Změny zabezpečení v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204496"
---
# <a name="security-changes-in-the-net-framework"></a>Změny zabezpečení v rozhraní .NET Framework

The most important change to security in the .NET Framework 4.5 is in strong naming. See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.  
  
The .NET Framework provides a two-tier security model for managed applications. Windows 8.x Store apps run in a Windows security container that limits access to resources. Within that container, managed applications run fully trusted. From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges. For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center. For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).
