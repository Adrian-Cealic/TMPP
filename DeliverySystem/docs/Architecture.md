# Delivery Management System - Laborator 1

## Arhitectura Sistemului

### Diagrama de Clase UML
![Class Diagram](http://www.plantuml.com/plantuml/svg/tVdLc9s2EL7zV-ykh1KylDjT8UXjOpHlONXUadTITo8ZiIQtVCDAAKBdNfV_7wJ8gSTk8WRaHTQk9oFvv13sgm-1IcoUGYcLytk9Vfv1XhuafVlwovUFI3eKZFFkmOG0UYEPRJA7mlFhoFSHKTgDqCwgviIbqYiRCl6PokjvmMiJFSRWbW6MYpvC0GUixZr9TeG4r3IphVmbPe66kTyNopwkO9wTXlzIjDABV2RP1Qv4FgH-3B_ZaKNIYkp7eCcQ9P6caFop2d8PsExn8L5gabM0nTaPR55RPAovs8q-I_5aEK5juflzBvhHE_NmNEPckntK76n5hejtQqboewZMGCd8bAMocS8KbWRGlYd6Cr-RjM4A42Pizlt-h1TwwPpqK0VIf56mimo9qx_CJNQIYoG7ToDaTSaQW58TIKWlH_6aGovPqdebYoT30mPZaTm4MfVBB_Uc_Dj3gwjqVVHEpBeWrzzg96NKe-R-YVjBaH3FtDl14iUunHkaNSPD4oG1IaZAY2dXvviGihJD07mZwQU-XLOMetKbPO1L34RT4rzHSQ-GnwQM3aKObSwVGvs-5O0TzeQ9fZ5uCbCMKhb0IRDs0AgL_VoawleKJa7UU5qwjPCAyh-U3W1NXyecMovQS9sRrJRMi8QEj8YR_F4Qd2jbk1aFJJhxyEK4SjxDyTAXjr-8RTCBr9WGEyjqLSbw4ByO_id2eh1vIQvFntc4DjWIpZ7f4-kkG057DaxDwbd650f4TLcs4fR6n6OF9xLW_kD-OsRxR29BeFJwrL165NizEad4QIlI6K9ZY47kWNE6J6LXG-o44mDruBHkCYUFEQui1D5-6IL1u_qgSs_Zjg5TcPQchoa0wM9w8vI4zL63UdWiXascdQL4Tv6G44ioUF1dYfUKTVd2j8Dp--6Yjw8F3eLwY54A94D8Jww0JeKHGPNAvE-Omeau5LNWto7hEKkie2K8NLez_oSZa83uxMERs2LJjqY3-YEZU_s9OITwQjdgzL-AaIMrOMN8lltCD0yzWjmWJR8TSGoCJtCmaNSpFrWb6zrYwJEtFepwDyosxbUiQjNzUKNh5KDGJTaOnniQ_uomAqennwkv6Ed3Kzw76zSGtVGUmsDpWbi5NVheSWSG2wtkyEYWwqihWYf4-sKk3c5Iu5tXeePXJcK66U2sy4Lz2nbU2cILnIoi828GXqzVNah9l-KWqcxbwWGeoHcf-SdK0v2lVHW1NIKlGCw1SWu3sDXEOR3kx8HsHicP6YqK1AdRV1yrUFWYh6aqqCfAlBUTROI1Rw_GOUv2uOpFoyrrxyj6EffcUsXcMQFFsScxKfSW5TryvnpO_5m2N9eBwCVqqF6ew8F6Q3g9C9yqN4i6grZZW7QLmWGJMQvyFfIpE-YA95A33z3jafOhAjPYEh2VV_ZxjdrdBGdYqsLgl2Atnk7P2m8nnNOUS3GnwUhP7ldn6bpp040YBbdSdQV1cDMgVT1Yvx2VXkWV3ms7q-AnupRGQhrMn52BIG8b7gHG43nnZjceR7aqMqQKVw3VeKdtCgBFRKR4iPk-kyrfMp1FWMRgnfe38BMG_gQ-2dmSX-eU4gj6CTImXu0Ou_HS2_Vy7Lt5_fJk6OgtPhYZ_xc=)

### Structura Proiectului

```
DeliverySystem/
├── DeliverySystem.Domain/           # Entități și logică de business
│   ├── Entities/
│   │   ├── EntityBase.cs            # Clasă abstractă de bază
│   │   ├── Customer.cs              # Moștenește EntityBase
│   │   ├── Order.cs                 # Moștenește EntityBase
│   │   ├── OrderItem.cs             # Value object pentru item-uri
│   │   ├── Courier.cs               # Clasă abstractă pentru curieri
│   │   ├── BikeCourier.cs           # Moștenește Courier (polimorfism)
│   │   ├── CarCourier.cs            # Moștenește Courier (polimorfism)
│   │   └── Delivery.cs              # Moștenește EntityBase
│   ├── Enums/
│   │   ├── OrderStatus.cs
│   │   ├── DeliveryStatus.cs
│   │   └── VehicleType.cs
│   └── ValueObjects/
│       └── Address.cs               # Value object imutabil
│
├── DeliverySystem.Interfaces/       # Abstracții (DIP)
│   ├── ICustomerRepository.cs
│   ├── IOrderRepository.cs
│   ├── ICourierRepository.cs
│   ├── IDeliveryRepository.cs
│   └── INotificationService.cs
│
├── DeliverySystem.Services/         # Logică de aplicație (SRP)
│   ├── OrderService.cs              # Gestionare comenzi
│   └── DeliveryService.cs           # Gestionare livrări
│
├── DeliverySystem.Infrastructure/   # Implementări concrete
│   ├── Repositories/
│   │   ├── InMemoryCustomerRepository.cs
│   │   ├── InMemoryOrderRepository.cs
│   │   ├── InMemoryCourierRepository.cs
│   │   └── InMemoryDeliveryRepository.cs
│   └── Notifications/
│       └── ConsoleNotificationService.cs
│
└── DeliverySystem.Console/          # Aplicație demonstrativă
    └── Program.cs                   # DOAR wiring + demo
```

## Principii OOP Demonstrate

### 1. Encapsulare
- Toate câmpurile sunt `private`
- Acces prin proprietăți publice cu validare
- Colecții expuse ca `IReadOnlyList`

```csharp
public class Customer : EntityBase
{
    public string Name { get; private set; }  // Encapsulare
    
    public void SetName(string name)          // Validare în setter
    {
        if (string.IsNullOrWhiteSpace(name))
            throw new ArgumentException("Customer name cannot be empty.");
        Name = name;
    }
}
```

### 2. Moștenire

```
EntityBase (abstract)
    ├── Customer
    ├── Order
    ├── Courier (abstract)
    │       ├── BikeCourier
    │       └── CarCourier
    └── Delivery
```

### 3. Polimorfism

```csharp
// Courier.cs - metode abstracte
public abstract class Courier : EntityBase
{
    public abstract decimal MaxWeight { get; }
    public abstract TimeSpan CalculateDeliveryTime(decimal distanceKm);
}

// BikeCourier.cs - implementare specifică
public class BikeCourier : Courier
{
    public override decimal MaxWeight => 5.0m;
    public override TimeSpan CalculateDeliveryTime(decimal distanceKm)
    {
        return TimeSpan.FromMinutes((double)(distanceKm * 3.0m));  // 3 min/km
    }
}

// CarCourier.cs - implementare specifică
public class CarCourier : Courier
{
    public override decimal MaxWeight => 50.0m;
    public override TimeSpan CalculateDeliveryTime(decimal distanceKm)
    {
        return TimeSpan.FromMinutes((double)(distanceKm * 1.5m));  // 1.5 min/km
    }
}
```

## Principii SOLID Demonstrate

### SRP (Single Responsibility Principle)
Fiecare clasă are o singură responsabilitate:
- `OrderService` - gestionează comenzi
- `DeliveryService` - gestionează livrări
- `Customer` - reprezintă un client
- `Order` - reprezintă o comandă

### OCP (Open/Closed Principle)
- `Courier` este deschis pentru extensie (poate adăuga `TruckCourier`)
- Închis pentru modificare (nu trebuie să schimbăm codul existent)

### LSP (Liskov Substitution Principle)
- `BikeCourier` și `CarCourier` pot înlocui `Courier` peste tot
- Comportamentul polimorfic respectă contractul clasei de bază

### ISP (Interface Segregation Principle)
- Interfețe mici și focusate
- `IOrderRepository` - doar metode pentru Order
- `ICourierRepository` - doar metode pentru Courier

### DIP (Dependency Inversion Principle)
- Serviciile depind de interfețe, nu implementări concrete
- Injecție de dependențe prin constructor

```csharp
public class OrderService
{
    private readonly IOrderRepository _orderRepository;      // Interfață, nu implementare
    private readonly ICustomerRepository _customerRepository;
    private readonly INotificationService _notificationService;

    public OrderService(
        IOrderRepository orderRepository,                    // Injecție prin constructor
        ICustomerRepository customerRepository,
        INotificationService notificationService)
    {
        _orderRepository = orderRepository;
        _customerRepository = customerRepository;
        _notificationService = notificationService;
    }
}
```

## Relații între Entități

| Relație | Tip | Descriere |
|---------|-----|-----------|
| Customer → Address | Compoziție | Customer conține Address |
| Order → OrderItem | Compoziție | Order conține lista de OrderItem |
| Order → Customer | Asociere | Order aparține unui Customer |
| Delivery → Order | Asociere | Delivery este pentru un Order |
| Delivery → Courier | Asociere | Delivery este asignat unui Courier |
| BikeCourier → Courier | Moștenire | BikeCourier extinde Courier |
| CarCourier → Courier | Moștenire | CarCourier extinde Courier |

## Fluxul Aplicației

1. **Creare Customer** cu Address
2. **Creare Order** cu OrderItems
3. **Confirmare și Procesare** Order
4. **Selectare Courier** disponibil (polimorfism)
5. **Creare Delivery** și asignare Courier
6. **Actualizare Status** Delivery (PickedUp → InTransit → Delivered)
7. **Notificări** către Customer
