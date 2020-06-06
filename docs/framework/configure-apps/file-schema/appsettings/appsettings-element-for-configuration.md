---
title: <appSettings> – element pro <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155528"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="7b18a-102">\<appSettings> – element pro \<configuration></span><span class="sxs-lookup"><span data-stu-id="7b18a-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="7b18a-103">Obsahuje vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-103">Contains custom application settings.</span></span> <span data-ttu-id="7b18a-104">Toto je předdefinovaný konfigurační oddíl poskytnutý .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b18a-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="7b18a-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="7b18a-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7b18a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b18a-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="7b18a-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b18a-107">Attribute</span></span>

|           | <span data-ttu-id="7b18a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7b18a-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="7b18a-109">**souborů**</span><span class="sxs-lookup"><span data-stu-id="7b18a-109">**file**</span></span>  | <span data-ttu-id="7b18a-110">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7b18a-110">Optional attribute.</span></span><br><br><span data-ttu-id="7b18a-111">Určuje relativní cestu k externímu souboru, který obsahuje vlastní nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="7b18a-112">Zadaný soubor obsahuje stejný druh nastavení, které jsou zadány v **\<add>** **\<remove>** prvcích, a **\<clear>** a používá stejný formát dvojice klíč/hodnota jako tyto prvky.</span><span class="sxs-lookup"><span data-stu-id="7b18a-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="7b18a-113">Zadaná cesta je relativní vzhledem k hlavnímu konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="7b18a-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="7b18a-114">V případě aplikace model Windows Forms se jedná o binární složku (například */bin/Debug*), nikoli o umístění konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="7b18a-115">Pro aplikace webových formulářů je cesta relativní k kořenovému adresáři aplikace, kde je umístěn soubor *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="7b18a-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="7b18a-116">Modul runtime ignoruje atribut, pokud zadaný soubor nelze nalézt.</span><span class="sxs-lookup"><span data-stu-id="7b18a-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="7b18a-117">Nadřazený element</span><span class="sxs-lookup"><span data-stu-id="7b18a-117">Parent element</span></span>

|     | <span data-ttu-id="7b18a-118">Description</span><span class="sxs-lookup"><span data-stu-id="7b18a-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7b18a-119">**\<configuration>** Objekt</span><span class="sxs-lookup"><span data-stu-id="7b18a-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="7b18a-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b18a-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7b18a-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7b18a-121">Child elements</span></span>

|     | <span data-ttu-id="7b18a-122">Description</span><span class="sxs-lookup"><span data-stu-id="7b18a-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="7b18a-123">Přidá vlastní nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="7b18a-124">Vymaže všechna dříve definovaná nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="7b18a-125">Odebere dříve definované nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7b18a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b18a-126">Remarks</span></span>

<span data-ttu-id="7b18a-127">**\<appSettings>** Element ukládá vlastní informace o konfiguraci aplikace, například připojovací řetězce k databázi, cesty k souborům, adresy URL webových služeb XML nebo jakékoli další vlastní informace o konfiguraci pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7b18a-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="7b18a-128">Páry klíč/hodnota zadané v **\<appSettings>** elementu jsou k dispozici v kódu pomocí <xref:System.Configuration.ConfigurationSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b18a-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="7b18a-129">Můžete použít atribut **File** v **\<appSettings>** prvku souboru *Web. config* a konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="7b18a-130">Tento atribut určuje konfigurační soubor, který poskytuje další nastavení nebo přepisuje nastavení zadané v **\<appSettings>** elementu.</span><span class="sxs-lookup"><span data-stu-id="7b18a-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="7b18a-131">Atribut **File** lze použít ve scénářích vývoje týmu správy zdrojového kódu, například když chce uživatel přepsat nastavení projektu zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="7b18a-132">Konfigurační soubory určené atributem **souboru** musí mít kořenový uzel, **\<appSettings>** nikoli **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="7b18a-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="7b18a-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b18a-133">Example</span></span>

<span data-ttu-id="7b18a-134">Následující příklad ukazuje soubor nastavení externí aplikace (*Custom. config*), který definuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="7b18a-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="7b18a-135">Následující příklad ukazuje konfigurační soubor aplikace, který využívá nastavení v souboru externího nastavení a nastavuje vlastní nastavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="7b18a-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="7b18a-136">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="7b18a-136">Configuration file</span></span>

<span data-ttu-id="7b18a-137">Tento element lze použít v konfiguračním souboru aplikace, konfiguračním souboru počítače (*Machine. config*) a souborech *Web. config* , které nejsou na úrovni adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b18a-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b18a-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b18a-138">See also</span></span>

- [<span data-ttu-id="7b18a-139">Schéma konfiguračního souboru pro .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b18a-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
