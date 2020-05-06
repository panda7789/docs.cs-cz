---
title: Nepodporovaná rozhraní API v .NET Core
titleSuffix: ''
description: Seznamte se s rozhraními API z .NET Framework, která vždy vyvolají výjimku pro .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 941e9149c7679afe4a888149108d0a9a28e5e7ab
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794595"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>Rozhraní API, která vždy vyvolávají výjimky v .NET Core

Následující rozhraní API se vždy vyvolají <xref:System.PlatformNotSupportedException> na .NET Core ve všech nebo v podmnožině platforem.

Tento článek uspořádá ovlivněné členy rozhraní API podle oboru názvů.

> [!NOTE]
>
> - Tento článek je nedokončený. Nejedná se o úplný seznam rozhraní API, která vyvolávají výjimky v rozhraní .NET Core.
> - Tento článek nezahrnuje implementace explicitního rozhraní pro binární serializaci, která se vyvolává v .NET Core. Další informace najdete v tématu [binární serializace v .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>Systém

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Vše |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Vše |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Vše |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Vše |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Vše |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Vše |

## <a name="systemcodedomcompiler"></a>System. CodeDom. Compiler

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Vše |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Vše |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Vše |

## <a name="systemcollectionsspecialized"></a>System. Collections. specialize

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Vše |

## <a name="systemconfiguration"></a>System. Configuration

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(všichni členové) | Vše |

## <a name="systemconsole"></a>System. Console

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType>(jenom pro Get) | Linux a macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Console.Title?displayProperty=nameWithType>(jenom pro Get) | Linux a macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |

## <a name="systemdatacommon"></a>System. data. Common

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(vyvolá <xref:System.NotSupportedException>) | Vše |

## <a name="systemdiagnosticsprocess"></a>System. Diagnostics. Process

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(jenom nastavit) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(jenom nastavit) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(jenom pro Get) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |

## <a name="systemio"></a>System.IO

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |

## <a name="systemiopipes"></a>System. IO. Pipes

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(jenom nastavit) | Linux a macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux a macOS |

## <a name="systemmedia"></a>System. Media

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |

## <a name="systemnet"></a>System.Net

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Vše |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |

## <a name="systemnetnetworkinformation"></a>System .NET. NetworkInformation

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP) |

## <a name="systemnetsockets"></a>System .NET. Sockets

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | Vše |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Vše |

## <a name="systemnetwebsockets"></a>System .NET. WebSockets

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Vše |

## <a name="systemreflection"></a>System. Reflection

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Vše |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Vše |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | Vše |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Vše |

## <a name="systemruntimecompilerservices"></a>System. Runtime. CompilerServices

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Vše |

## <a name="systemruntimeinteropservices"></a>System. Runtime. InteropServices

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Vše |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Vše |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Vše |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Vše |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux a macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Vše |

## <a name="systemsecurity"></a>System. Security

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Vše |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Vše |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Vše |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Vše |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Vše |

## <a name="systemsecurityclaims"></a>System. Security. Claims

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | Vše |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | Vše |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |

## <a name="systemsecuritycryptography"></a>System. Security. Cryptography

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux a macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Vše |

## <a name="systemsecuritycryptographypkcs"></a>System. Security. Cryptography. PKCS

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | Vše |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Vše |

## <a name="systemsecuritycryptographyx509certificates"></a>System. Security. Cryptography. X509Certificates

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(jenom nastavit) | Vše |

## <a name="systemsecurityauthenticationextendedprotection"></a>System. Security. Authentication. ExtendedProtection

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |

## <a name="systemsecuritypolicy"></a>System. Security. Policy

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |

## <a name="systemserviceprocessservicecontroller"></a>System. ServiceProcess. ServiceController

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | Vše |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Vše |

## <a name="systemthreading"></a>System. Threading

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Vše |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Vše |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Vše |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Vše |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Vše |

## <a name="systemxml"></a>System.Xml

| Člen | Platformy, které vyvolávají výjimku |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Vše |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Vše |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Vše |

## <a name="see-also"></a>Viz také

- [Zásadní změny migrace z .NET Framework do .NET Core](fx-core.md)
- [Binární serializace v .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Analyzátor přenositelnosti .NET](../../standard/analyzers/portability-analyzer.md)
