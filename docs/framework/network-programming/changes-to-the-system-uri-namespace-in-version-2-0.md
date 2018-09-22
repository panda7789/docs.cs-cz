---
title: Změny v oboru názvů System.Uri ve verzi 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f300ab05f28feca8baa13c4078df622e1e7d9d19
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46579443"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Změny v oboru názvů System.Uri ve verzi 2.0

Bylo provedeno několik změn <xref:System.Uri?displayProperty=nameWithType> třídy. Tyto změny oprava nesprávné chování, rozšířeného použitelnost a zvýšené zabezpečení.

## <a name="obsolete-and-deprecated-members"></a>Zastaralé a již zastaralé členy

 Konstruktory:

- Všechny konstruktory, které mají `dontEscape` parametru.

 Metody:

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a>Změny

- Pro schémata identifikátoru URI, které se ví, že není nutné část dotazu (souboru, protokolu ftp a dalších) "?" znak je vždy uvozen řídicími znaky a není považováno za začátek <xref:System.Uri.Query%2A> část.

- Implicitní souboru identifikátory URI (ve formátu `c:\directory\file@name.txt`), fragment znak (#) je vždy uvozen řídicími znaky, pokud je požadována úplná unescaping nebo <xref:System.Uri.LocalPath%2A> je `true`.

- Byla odebrána podpora UNC hostname; byla přijata specifikaci IDN představující mezinárodní názvy hostitelů.

- <xref:System.Uri.LocalPath%2A> vždy vrátí řetězec zcela bez řídících znaků.

- <xref:System.Uri.ToString%2A> není unescape s uvozovacími znaky "%", "?", nebo znak "#".

- <xref:System.Uri.Equals%2A> nyní zahrnuje <xref:System.Uri.Query%2A> část v kontrole rovnosti.

- Operátory "=="a"! =" jsou přepsat a že propojení se <xref:System.Uri.Equals%2A> metody.

- <xref:System.Uri.IsLoopback%2A> nyní poskytuje konzistentní výsledky.

- Identifikátor URI "`file:///path`" je již přeloženy do `file://path`.

- "#" nyní považována za zakončením název hostitele. To znamená `http://contoso.com#fragment` je nyní převést na `http://contoso.com/#fragment`.

- Opravili jsme chybu při kombinování základní identifikátor URI s fragmentem.

- Chyba v <xref:System.Uri.HostNameType%2A> vyřešen.

- Chyba při analýze NNTP opravena.

- Identifikátor URI ve formátu HTTP:contoso.com nyní výjimku analýzy.

- Rozhraní správně zpracovává informací o uživateli v identifikátoru URI.

- Komprese cesty identifikátoru URI je vyřešen tak, aby přerušení identifikátor URI nelze procházení systému souborů kořenem.

## <a name="see-also"></a>Viz také:

- <xref:System.Uri?displayProperty=nameWithType>
